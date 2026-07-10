Platform AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start EXPLORE Why GitHub Documentation Blog Changelog Marketplace View all features

AI CODE CREATION GitHub Copilot Write better code with AI GitHub Copilot app Direct agents from issue to merge MCP Registry New Integrate external tools

GitHub Copilot Write better code with AI

GitHub Copilot app Direct agents from issue to merge

MCP Registry New Integrate external tools

DEVELOPER WORKFLOWS Actions Automate any workflow Codespaces Instant dev environments Issues Plan and track work Code Review Manage code changes

Actions Automate any workflow

Codespaces Instant dev environments

Issues Plan and track work

Code Review Manage code changes

APPLICATION SECURITY GitHub Advanced Security Find and fix vulnerabilities Code security Secure your code as you build Secret protection Stop leaks before they start

GitHub Advanced Security Find and fix vulnerabilities

Code security Secure your code as you build

Secret protection Stop leaks before they start

EXPLORE Why GitHub Documentation Blog Changelog Marketplace

Solutions BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries View all solutions

BY COMPANY SIZE Enterprises Small and medium teams Startups Nonprofits

Small and medium teams

BY USE CASE App Modernization DevSecOps DevOps CI/CD View all use cases

BY INDUSTRY Healthcare Financial services Manufacturing Government View all industries

Resources EXPLORE BY TOPIC AI Software Development DevOps Security View all topics EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners View all resources

EXPLORE BY TOPIC AI Software Development DevOps Security View all topics

Software Development

EXPLORE BY TYPE Customer stories Events & webinars Ebooks & reports Business insights GitHub Skills

SUPPORT & SERVICES Documentation Customer support Community forum Trust center Partners

Open Source COMMUNITY GitHub Sponsors Fund open source developers PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program REPOSITORIES Topics Trending Collections

COMMUNITY GitHub Sponsors Fund open source developers

GitHub Sponsors Fund open source developers

PROGRAMS Security Lab Maintainer Community Accelerator GitHub Stars Archive Program

Maintainer Community

REPOSITORIES Topics Trending Collections

Enterprise ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

ENTERPRISE SOLUTIONS Enterprise platform AI-powered developer platform

Enterprise platform AI-powered developer platform

AVAILABLE ADD-ONS GitHub Advanced Security Enterprise-grade security features Copilot for Business Enterprise-grade AI features Premium Support Enterprise-grade 24/7 support

GitHub Advanced Security Enterprise-grade security features

Copilot for Business Enterprise-grade AI features

Premium Support Enterprise-grade 24/7 support

Search code, repositories, users, issues, pull requests...

We read every piece of feedback, and take your input very seriously.

Use saved searches to filter your results more quickly

To see all available qualifiers, see our documentation .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Notifications You must be signed in to change notification settings

Security and quality 0

Security and quality

Repository files navigation

This Sovereign AI Landing Zone (SAIL) repository provides a secure foundation for deploying AI models within Canada’s borders on Azure, so organizations can build, scale, and innovate while maintaining the highest standards of privacy and compliance. As the initial focus, we consider sovereignty on Azure as satisfying two key requirements:

Data at rest should be stored within Canadian Azure data centres

Data in-transit should be processed within Canadian Azure data centres

The critical Azure services in supporting the deployment of sovereign AI models in Canada are Microsoft Foundry , Azure Machine Learning , and Azure Databricks .

We will provide a comprehensive review of deployment approaches and templates for AI models satisfying the two soverignity requirements of data at rest and in-transit staying within Canada borders.

Initial Azure Bicep scripts for deployment of Azure Machine Learning, Microsoft Foundry, and Azure Databricks through Infrastructure as Code (IaC) can be found in the infra folder. SAIL does not go deep into the architecture and design on AI landing zones themselves, rather it is focused on sovereign AI models deployment and configurations. See this official repo Azure AI Landing Zones for its reference architecture and implementation details.

Microsoft Foundry AI model deployment options

For soverignity reasons, it would be important to consider AI models deployable within Microsoft Foundry from the list of Directly Sold by Azure models which satisfy deployment requirements from a data security and privacy perspective as outlined here .

In particular for models from the Directly Sold by Azure list within Microsoft Foundry:

Data at rest is stored in the Foundry resource in the customer's Azure tenant, within the same geography as the resource. For Canada, the geography is Canada Central and Canada East . Generally prompts and completions for such models are not stored except as part of specific features such as fine-tuning and Assistant API. Another default-enabled temporary data storage feature is to defend against abuse where potentially abusive material from prompts and completions may be stored up to 30 days for the sole purpose of Microsoft review. This feature can be disabled by submitting this form .

Data at rest is stored in the Foundry resource in the customer's Azure tenant, within the same geography as the resource. For Canada, the geography is Canada Central and Canada East . Generally prompts and completions for such models are not stored except as part of specific features such as fine-tuning and Assistant API. Another default-enabled temporary data storage feature is to defend against abuse where potentially abusive material from prompts and completions may be stored up to 30 days for the sole purpose of Microsoft review. This feature can be disabled by submitting this form .

Data in-transit can be processed in various forms depending on the model deployment type . To ensure that AI models through AI Foundry process data in-transit within Canadian Azure regions, they must be deployed as either Standard for Pay-As-You-Go deployments Regional Provisioned for Provisioned Throughput Unit - PTU (dedicated capacity with guaranteed units of throughput) deployments

Data in-transit can be processed in various forms depending on the model deployment type . To ensure that AI models through AI Foundry process data in-transit within Canadian Azure regions, they must be deployed as either

Standard for Pay-As-You-Go deployments

Regional Provisioned for Provisioned Throughput Unit - PTU (dedicated capacity with guaranteed units of throughput) deployments

Alternatively, global deployment type means that data might be processed for inferencing in any Foundry location in the world. Data zone is not applicable for Canada as only US and Europe regions have Data Zone support .

Alternatively, global deployment type means that data might be processed for inferencing in any Foundry location in the world. Data zone is not applicable for Canada as only US and Europe regions have Data Zone support .

As of May 25, 2026, these are the models within AI Foundry that provide guaranteed data in-transit processing within Canada: Standard for Pay-As-You-Go deployments (available through Microsoft Foundry deployed in Canada East region): gpt-4.1-mini gpt-4o (Version 1120) text embedding models (ada, 3-large, 3-small) Regional Provisioned Throughput Units (PTU) deployments (available through Microsoft Foundry deployed in Canada East region): o3-mini gpt-5-mini gpt-5 gpt-5.1 gpt-5.2 (only available in Canada Central) gpt-4o (Versions 1120, 0806, 0513 - also available in Canada Central) gpt-4o-mini

As of May 25, 2026, these are the models within AI Foundry that provide guaranteed data in-transit processing within Canada:

Standard for Pay-As-You-Go deployments (available through Microsoft Foundry deployed in Canada East region): gpt-4.1-mini gpt-4o (Version 1120) text embedding models (ada, 3-large, 3-small)

gpt-4o (Version 1120)

text embedding models (ada, 3-large, 3-small)

Regional Provisioned Throughput Units (PTU) deployments (available through Microsoft Foundry deployed in Canada East region): o3-mini gpt-5-mini gpt-5 gpt-5.1 gpt-5.2 (only available in Canada Central) gpt-4o (Versions 1120, 0806, 0513 - also available in Canada Central) gpt-4o-mini

gpt-5.2 (only available in Canada Central)

gpt-4o (Versions 1120, 0806, 0513 - also available in Canada Central)

There are also many AI models that could be deployed using the Microsoft Foundry (classic) hub-based service using managed compute, such as certain Cohere models from the Directly Sold by Azure list. Such models would be deployed on managed GPU VMs to ensure data in-transit and data at rest remains in Canada geography in a Hub-based Foundry resource, which is based on the Azure ML deployment infrastructure as seen below. Just remember to set the Azure ML deployment script as kind: 'hub' .

There are also many AI models that could be deployed using the Microsoft Foundry (classic) hub-based service using managed compute, such as certain Cohere models from the Directly Sold by Azure list. Such models would be deployed on managed GPU VMs to ensure data in-transit and data at rest remains in Canada geography in a Hub-based Foundry resource, which is based on the Azure ML deployment infrastructure as seen below. Just remember to set the Azure ML deployment script as kind: 'hub' .

Azure Machine Learning AI model deployment options

The following is guidance to facilitate deployment of generic AI models including large language models (LLMs) on Azure Machine Learning's (AML) Managed Online Endpoints for efficient, scalable, and secure real-time inference.​ Two patterns of deployment types are described: models through vLLM and generic AI models. By leveraging AML's Managed Online Endpoints , the model would be deployed within the AML region and secured through inbound and outbound private connections thus ensuring a secured and sovereign solution. The AI model is deployed in a managed virtual network within the region of the Azure ML service, which should be in Canada Central.

In particular, this pattern gives you the ability to utilize OOTB Hugging Face models onto Managed Online Endpoints in AML, using managed compute.

vLLM: A high-throughput, memory-efficient inference engine designed for LLMs.​ We will be creating a custom Dockerized environment for vLLM on AML as a foundational step.

(Optional) You can also bring in any generic AI models by leveraging the custom Dockerfile and providing a generic score.py file that loads the model in memory and defines inferencing.

Managed Online Endpoints: A feature in Azure Machine Learning that simplifies deploying machine learning models for real-time inference by handling serving, scaling, securing, and monitoring complexities.​ At the time of writing, an additional context to using this feature is to ensure data and regional residency abilities that could be achieved through the setup here.

Model of your choice from HuggingFace (or any generic AI model). Knowledge around usage of HuggingFace models and the workflow and AuthN aspects are assumed.

Key Deployment Steps:

Create a Custom Environment on AzureML: Define a Dockerfile specifying the environment for the model, utilizing vLLM's base container with necessary dependencies.​

Create a Custom Environment on AzureML: Define a Dockerfile specifying the environment for the model, utilizing vLLM's base container with necessary dependencies.​

Deploy the AzureML Managed Online Endpoint: Configure the endpoint and deployment settings using YAML files, specifying the model to deploy, environment variables, and instance configurations.​

Deploy the AzureML Managed Online Endpoint: Configure the endpoint and deployment settings using YAML files, specifying the model to deploy, environment variables, and instance configurations.​

Test the Deployment: Retrieve the endpoint's scoring URI and API keys, then send test requests to ensure the model is serving correctly.​ Using MS Entra for authentication and authorization is supported as well: https://learn.microsoft.com/en-us/azure/machine-learning/concept-endpoints-online-auth?view=azureml-api-2

Test the Deployment: Retrieve the endpoint's scoring URI and API keys, then send test requests to ensure the model is serving correctly.​ Using MS Entra for authentication and authorization is supported as well: https://learn.microsoft.com/en-us/azure/machine-learning/concept-endpoints-online-auth?view=azureml-api-2

(Optional) Autoscale the AML Endpoint: Set up autoscaling rules to dynamically adjust the number of instances based on real-time metrics, ensuring efficient handling of varying loads.​

(Optional) Autoscale the AML Endpoint: Set up autoscaling rules to dynamically adjust the number of instances based on real-time metrics, ensuring efficient handling of varying loads.​

For pre-trained Foundry large language models, as long as these models offer a managed compute deployment option, you can use the model deployment wizard or follow the guide here: https://learn.microsoft.com/en-us/azure/foundry-classic/how-to/deploy-models-managed?pivots=ai-foundry-portal though note that for private and security reasons, the managed compute endpoint should always be set to use private endpoint (which is the default configuration in this repo).

For pre-trained Foundry large language models, as long as these models offer a managed compute deployment option, you can use the model deployment wizard or follow the guide here: https://learn.microsoft.com/en-us/azure/foundry-classic/how-to/deploy-models-managed?pivots=ai-foundry-portal though note that for private and security reasons, the managed compute endpoint should always be set to use private endpoint (which is the default configuration in this repo).

Essence of the steps via code/CLI commands:

Deploy to Managed Online Endpoint

Get API endpoint and API keys

Test the model using the test_model.py file

Azure Databricks AI deployment options

Details on Azure Databricks soverign AI options within Canada regions can be found here: Deploying Azure Databricks AI for Canadian Data Residency .

Special thanks to the following individuals for their invaluable contributions to this repo:

Shankar Ramachandran: https://github.com/shankar-r10n

Amy Xin: https://github.com/amyxixin

Sherif Messiha: https://github.com/shmessiha

This project welcomes contributions and suggestions. Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit Contributor License Agreements .

When you submit a pull request, a CLA bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the Microsoft Open Source Code of Conduct . For more information see the Code of Conduct FAQ or contact opencode@microsoft.com with any additional questions or comments.

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow Microsoft's Trademark & Brand Guidelines . Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party's policies.

The Sovereign AI Landing Zone deployment template is an open-source Infrastructure as Code (IaC) solution designed to deploy LLM models to run completely within an Azure region. This template enables organizations—especially those in highly regulated industries—to implement LLMs on Azure with full data and compute sovereignty

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

There was an error while loading. Please reload this page .

Do not share my personal information