Microsoft Community Hub

Communities Products Microsoft Security

Microsoft Sentinel Blog

Introducing the next generation of SOC automation: Sentinel playbook generator

Security teams today operate under constant pressure. They are expected to respond faster, automate more, and do so without sacrificing precision. Traditional security orchestration, automation and response (SOAR) approaches have helped, but they still rely heavily on rigid templates, limited action libraries, and workflows stretched across multiple portals. Building and maintaining automation is often slow and constrained at exactly the time organizations need more flexibility. Something needs to change – and with the introduction of AI and coding models the future of automation is going to look very different than it is today.

Today, we’re introducing the Microsoft Sentinel playbook generator (now Generally Available) , a new way to design code-based playbooks using natural language. With the introduction of generative AI and coding models, coding itself is becoming democratized, and we are excited to bring these new capabilities into our experience. This release represents the first milestone in our next‑generation security automation journey.

The playbook generator allows users to design and generate fully functional playbooks simply by describing what they need. The tool generates a Python playbook with documentation and a visual flowchart, streamlining workflows from creation to execution for greater efficiency.

This approach is highly flexible, allowing users to automate tasks like team notifications, ticket updates, data enrichment, or incident response across Microsoft and third-party tools. By defining an Integration Profile (base URL, authentication, credentials), the playbook generator can create API calls dynamically without needing predefined connectors. The system also identifies missing integrations and guides users to add them from the Automation tab or within the authoring page Users especially value this capability, allowing for more advanced automations.

Playbook creation starts by outlining the workflow. The playbook generator asks questions, proposes a plan, then generates code and documentation once approved. Users can validate playbooks with real alerts and refine code anytime through chat instructions or manual edits. This approach combines the speed of natural language with transparent code, enabling engineers to automate efficiently without sacrificing control or flexibility.

Preview customers report that the playbook generator speeds up automation development, simplifies automations for teams, and enables flexible workflow customization without reliance on templates.

The playbook generator focuses on fast, intuitive, natural‑language‑driven automation creation, supported by a powerful coding foundation. It aligns with how security teams want to work: flexible, integrated, and deeply customizable.

We’re excited to see how customers will use this capability to simplify operations, eliminate repetitive work, and automate tasks that previously demanded deep engineering effort. This marks the start of a new chapter, as AI continues to evolve and reshape what’s possible in security automation.

With just a few prerequisites in place, you can begin creating code‑based automations through natural‑language conversations, directly inside the Microsoft Defender portal.

Here’s a quick guide to help you move from first steps to your first generated playbook:

Before you open your first chat in the playbook generator, the AI coding agent behind the playbook generator, confirm that your environment is ready:

Security Copilot enabled: Your tenant must have a Security Copilot workspace, configured to use a Europe or US-based capacity.

Sentinel workspace in the Defender portal: Ensure your Microsoft Sentinel workspace is onboarded to the Microsoft Defender portal.

To build and deploy generated playbooks, make sure you have the same permissions required to author Automation Rules—the Microsoft Sentinel Contributor role on the relevant workspaces or resource groups.

Integration profiles allow the playbook generator to create and execute any dynamic API calls—one of the most powerful capabilities of this new system.

Before you create your first playbook:

Go to Automation → Integration Profiles in the Defender portal.

Create a Graph API Integration

Create Integration to the services you want to have in the playbook (Microsoft Graph, ticketing tools, communication systems, third‑party providers, or others).

Provide the base URL, authentication method, and required credentials.

From the Automation tab :

Select Create → Generated Playbook .

Give your playbook a name.

3. The embedded Visual Studio Code window opens—

Start in plan mode by simply describing what you want your automation to do. Be explicit about:

What data to extract

What actions to perform

Any conditions or branches

Example prompt you can use:

“Based on the alert, extract the user principal name, check if the account exists in Entra ID, and if it does, disable the account, create a ticket in ServiceNow, and post a message to the security team channel.”

The playbook generator will guide the process, ask clarifying questions, propose a plan, and then—once approved—switch to Act mode to generate the full Python playbook, documentation with a visual flow diagram, and tests.

Completing your first playbook marks the beginning of a more intuitive, responsive, and intelligent automation experience—one where your expertise and AI work side by side to transform how your SOC operates. This is more than a new tool; it’s a foundation that will continue to evolve, adapt, and empower defenders as security automation enters its next era.

Watch a demo here: https://aka.ms/NLSOARDEMO

For deeper guidance, advanced scenarios, and end‑to‑end instructions, you can explore the full playbook generator documentation: Generate playbooks using AI in Microsoft Sentinel | Microsoft Learn

Microsoft Sentinel is an industry-leading SIEM & AI-first platform powering agentic defense across the entire security ecosystem.

Surface Laptop Studio 2

Copilot for organizations

Copilot for personal use

Explore Microsoft products

Microsoft Store support

Certified Refurbished

Microsoft Store Promise

Microsoft in education

Devices for education

Microsoft Teams for Education

Microsoft 365 Education

How to buy for your school

Educator training and development

Deals for students and parents

Microsoft Power Platform

Microsoft 365 Copilot

Support for AI marketplace apps

Microsoft Tech Community

Microsoft Marketplace

Privacy at Microsoft

Diversity and inclusion