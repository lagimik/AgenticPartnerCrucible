# Deploying hosted agents in Foundry Agent Service via Terraform

**Source:** https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/deploying-hosted-agents-in-foundry-agent-service-via-terraform/4560435
**Captured:** 2026-10-03
**Published:** 2026-10-01 (Microsoft Foundry Blog / Microsoft Community Hub)
**Author:** j_folberth
**Sample repository:** https://github.com/JFolberth/simple-hosted-agent-deploy-azapi

---

## Problem framing

Organizations already manage Azure infrastructure through Terraform, but
deploying Foundry hosted agents has required manual SDK calls or REST API
scripts outside that pipeline. This post brings hosted-agent deployment
into an existing Terraform/IaC workflow using the **AzAPI provider**, so
the entire Foundry stack (project, model, connections, identity, registry,
and the agent itself) can be versioned, reviewed, and deployed together.

Hosted agents abstract away agent-compute management — conceptually,
moving compute that might otherwise run on Azure Container Apps or Azure
Functions into Foundry-managed compute running a container image. This
specific approach requires Azure Container Registry to host the code
artifact (a separate prior post, "Deploying Foundry Hosted Agents from
Source," covers deploying directly from source instead).

## Why IaC for hosted agents

A hosted agent is, at its core, configuring/allocating infrastructure
resources behind Foundry — similar to configuring plan sizes for a product
like App Services. Defining it under IaC gives:
- Version control of the agent configuration alongside the rest of the
  Foundry stack.
- Repeatable CI/CD pipelines, with production considerations for remote
  state, approval controls, and image-version promotion.
- The ability to apply custom (Azure or organizational) policy over the
  codebase.

## Prerequisites

- Azure subscription with permission to create resources and role
  assignments.
- Access to a region/model deployment with sufficient quota for Foundry
  Hosted Agents.
- Azure CLI, Terraform, Git, and Docker installed; Docker must support
  building `linux/amd64` images.
- Permission to push images to Azure Container Registry and create agents
  in the Foundry project.

Hosted agents require a Linux AMD64 container image. On ARM-based
workstations (including Apple Silicon), explicitly target `linux/amd64`
with cross-platform emulation enabled:
```
docker build --platform linux/amd64 -t <registry-name>.azurecr.io/<image-name>:<tag>
```

## Process overview (Day 1 vs. Day n)

In many large organizations, agent deployment is decoupled from the
Foundry base architecture: the Foundry account, project, connections, and
model may be owned by a centralized platform team on a different lifecycle
than an individual agent owned by a development team — a chicken-and-egg
problem the post explicitly breaks down.

**Day 1:**
1. Deploy Foundry base architecture (Foundry Account, Foundry Project,
   Model, Project Connection, Application Insights).
2. Build and push code to Azure Container Registry.
3. Deploy the hosted agent pointed at the image in Azure Container
   Registry.

**Day n (ongoing updates):**
1. Build and push code to Azure Container Registry.
2. Deploy the hosted agent pointed at the new image.

Updating the hosted-agent configuration creates a new agent *version*
under the existing logical agent. Foundry manages version history; Terraform
manages the logical agent configuration (the `azapi_data_plane_resource`).
After each deployment, confirm the new version reaches an active state
before directing workloads to it. The sample assumes Azure Container
Registry is managed outside the Foundry lifecycle (many organizations
consolidate images into shared registries), though the example includes
registry deployment for illustration.

## Technical details: control plane vs. data plane

The Foundry project and its connections are Azure Resource Manager
control-plane resources (`Microsoft.CognitiveServices/accounts/projects`,
`.../connections`). The **logical agent is created through the Foundry
project's data-plane API**, while Foundry manages the supporting deployment
resources required to host it — in contrast to services represented
directly as ARM resources, such as App Service
(`Microsoft.Web/sites`) or Azure Container Apps
(`Microsoft.App/containerApps`).

The project and connection resources can be deployed via AzAPI or Bicep
(control plane). The next step — creating the agent — requires a
data-plane call. For Terraform, this is handled declaratively via the
**AzAPI provider's `azapi_data_plane_resource`**, which bridges Terraform to
service-specific data-plane HTTPS endpoints (the same model used for Key
Vault's secrets API, Azure AI Search's index API, and Synapse's workspace
pipeline API). Foundry also supports agent deployment via its SDKs and REST
API as alternatives.

## Terraform implementation sketch

```hcl
resource "azapi_data_plane_resource" "hosted_agent" {
  type = "Microsoft.Foundry/agents@v1"
  name = var.agent_name
  # AzAPI data-plane parents use the endpoint host/path without a URI scheme.
  parent_id = trimprefix(var.project_endpoint, "https://")
  body = {
    name = var.agent_name
    definition = {
      kind = "hosted"
      container_configuration = {
        image = var.image_uri
      }
      cpu    = var.cpu
      memory = var.memory
      protocol_versions = [
        {
          # The hosted container must implement this Foundry Responses contract.
          protocol = "responses"
          version  = "2.0.0"
        }
      ]
      environment_variables = merge(var.environment_variables, {
        AZURE_AI_MODEL_DEPLOYMENT_NAME = var.model_deployment_name
      })
      rai_config = {
        # Hosted agents require the full policy ARM ID; model deployments use its name.
        rai_policy_name = var.rai_policy_id
      }
    }
  }
}
```

Full reusable module: https://github.com/JFolberth/simple-hosted-agent-deploy-azapi/tree/main/simple_agent/azure/infra/modules/hosted_agent

## Deploying the sample

Clone the repository, reopen in the included dev container, authenticate
to Azure and select the target subscription, copy/update the example
Terraform variable files with environment-specific values, then run the
included deployment script (provisions base resources, builds/pushes the
container image, creates the hosted agent). Confirm the generated agent
version reaches an active state before invoking it. Refer to the
repository README for current commands, configuration values, and cleanup
steps.

## Conclusion

Hosted Agents in Foundry Agent Service run custom agent code on
Foundry-managed compute while reducing operational overhead for the
underlying hosting infrastructure. Using the AzAPI provider's
`azapi_data_plane_resource`, teams fold the logical agent deployment into
an existing Terraform workflow alongside the Foundry project, model,
connections, identity, and container registry it depends on. This is
especially useful when platform and application responsibilities are
separated: a platform team manages shared Foundry/Azure infrastructure
while application teams independently build, publish, and deploy new agent
container versions. With appropriate remote state, access controls,
image-versioning strategy, and deployment validation, the pattern extends
into a repeatable CI/CD workflow for both initial deployment and ongoing
updates.

## Authorship note

First-person practitioner post by a named Microsoft Foundry Blog author
referencing his own prior posts and a personal/linked GitHub sample repo
— practical engineering guidance rather than formal product documentation;
treat the sample repository as an illustrative starting point to adapt,
not a production-ready template (explicitly stated in the conclusion).
