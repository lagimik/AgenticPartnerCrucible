Microsoft Community Hub

Communities Products Microsoft Security

Microsoft Purview Blog

Microsoft Purview Referential Architecture Diagrams

The Microsoft Purview architecture diagrams provide a referential view of how data classification, sensitivity labeling, Data Loss Prevention (DLP) and Insider Risk operate across Microsoft 365 workloads. These diagrams are intended to help organisations understand where policy evaluation occurs, how signals flow between services, and how enforcement is applied consistently.

Rather than prescribing a single deployment model, the diagrams illustrate common architectural patterns used to protect sensitive data across endpoints, email, and collaboration services.

Classification: How Content Sensitivity Is Determined

This diagram shows how content is classified across Microsoft 365 workloads and connected locations.

Key points highlighted in the diagram:

Classification can occur in the client, in transport, or in the service, depending on workload and policy.

Multiple classifier types are supported, including Sensitive Information Types (SITs) - deterministic patterns and keywords, and several advanced classifier models such as Exact Data Match, document fingerprinting and trainable classifiers.

Classification informs about what's in the content and results are reused by downstream controls such as DLP, auto-labeling, data lifecycle management, eDiscovery and more.

Classification is performed real time or near real time as content is created, modified, or transmitted.

Classification acts as the core signal for Purview data protection. All enforcement decisions shown in later diagrams rely on these classification outcomes.

Sensitivity Labelling: A Unified Control Plane

The labeling diagram illustrates how sensitivity labels are applied and enforced consistently across Microsoft 365.

Key points highlighted in the diagram:

Labels are organizational signals. they are end user facing and provides a consistent approach in training users on data security hygiene. They are your unified control plane across your data estate.

Labels can be applied manually, with layered defaults, and/or automatically, depending on workload and configuration.

Labels travel with content across SharePoint, OneDrive, Teams, Outlook, Office apps and more.

Label configuration can enforce protections such as encryption, watermarking, external access controls, and DLP on label.

User changing label to lower priority is a signal signaling intent to share, with deviations addressed with Data Loss Prevention, Insider Risk Management and Adaptive Protection.

Label priority rules ensure predictable behavior when multiple labelling methods apply.

Sensitivity labels provide a single mechanism to express organizational intent for data protection, reducing the need for workload‑specific configuration.

Endpoint DLP: Enforcing Policy on Devices

This diagram focuses on how DLP policies are evaluated and enforced directly on user devices, including Windows and macOS.

Key points highlighted in the diagram:

Devices are onboarded to Microsoft 365 and Purview through standard management methods. No additional agent is required.

Content is classified locally (+ optionally in the cloud) and evaluated against DLP policies in real time.

User actions such as copying to removable media, uploading to cloud services, printing, or pasting into browsers are evaluated before completion.

Enforcement actions include audit, warning, or block, with activity logged centrally.

Just-In-Time (JIT) ensures that files requiring re-evaluation at egress - due to policy change, file created while offline or recently downloaded file - are reclassified and protected.

Endpoint DLP extends protection to scenarios where data may never reach a cloud service, helping reduce risk from local data exfiltration.

Exchange DLP: Email Classification and Enforcement

This diagram shows how classification and DLP are integrated into the Exchange email pipeline.

Key points highlighted in the diagram:

Email content can be classified in the Outlook client and in Exchange transport, depending on policy and client capability.

DLP evaluation occurs before delivery, with actions such as policy tips, warnings, blocking, or encryption; and also in transport to ensure protection at all layers.

Enforcement is applied regardless of which Outlook client is used.

All actions are logged for auditing and investigation.

This architecture ensures that sensitive information is evaluated and protected before email leaves the organisation.

SharePoint DLP: Protecting Files even before sharing

The SharePoint DLP diagram illustrates how DLP policies are enforced as files are uploaded, shared, and accessed in SharePoint and OneDrive.

Key points highlighted in the diagram:

Both new and existing files are evaluated when content becomes sensitive, whether the file was previously shared or not, and whether content was already accessed externally prior to becoming sensitive.

DLP enforcement is triggered when files are shared internally or externally, depending on policy configurations.

Guest access scenarios are explicitly evaluated, with enforcement occurring when external access is detected.

Alerts and incidents are generated when sensitive content is shared outside policy boundaries.

This approach allows organisations to enforce policy at the moment of risk, even if a file was uploaded or shared before it became sensitive.

Browser DLP: Protecting Data in Web and AI Scenarios (unmanaged device / managed app)

This diagram illustrates how Microsoft Purview enforces DLP when users access managed applications from unmanaged devices or personal browsers. It highlights how organisations can reduce data exfiltration risk without blocking access entirely.

Key points highlighted in the diagram:

Access decisions are enforced using Conditional Access, session controls, and browser enforcement.

Users may be required to switch to Edge for Business to access sensitive applications.

DLP policies evaluate uploads, downloads, copy, paste, and print actions in real time.

Enforcement actions include audit or block, based on content sensitivity and policy intent.

This architecture is especially relevant for BYOD, contractor, and partner access scenarios, where device control is limited but data risk remains high.

Browser DLP (Managed Device / Unmanaged App)

This diagram focuses on scenarios where users on managed corporate devices interact with consumer AI tools or unmanaged web applications.

Key points highlighted in the diagram:

Web traffic is evaluated inline using browser‑based DLP enforcement.

Sensitive text typed into AI prompts or files uploaded to unmanaged apps can be audited or blocked.

Enforcement applies across all Edge profiles, ensuring consistent policy application.

Users can continue general browsing while sensitive data flows remain protected.

Browser DLP extends Purview protection into modern AI and SaaS usage patterns that traditional endpoint or cloud DLP cannot fully address.

Insider Risk Management: Detecting and Investigating Risky Behaviour

This diagram shows how Microsoft Purview Insider Risk Management correlates signals across Microsoft 365 and non‑Microsoft sources to detect risky user behavior.

Key points highlighted in the diagram:

Signals are ingested from user activities, DLP, audit logs, communication compliance, Defender, and third‑party sources.

Risk indicators are evaluated against policies and thresholds to generate alerts.

Investigations are managed through cases, with escalation, confirmation, or dismissal workflows.

Adaptive protection can automatically adjust DLP controls based on user risk level.

Insider Risk Management enables organisations to move from reactive alerts to contextual investigations, balancing security, privacy, and compliance.

Data Protection for Microsoft 365 Copilot

This diagram explains how Copilot respects sensitivity labels, encryption, and tenant boundaries when generating responses.

Key points highlighted in the diagram:

Copilot only accesses data within the Microsoft 365 service boundary.

Sensitivity labels and encryption are inherited by Copilot‑generated content.

External files opened in Office apps are evaluated independently from tenant data.

Exported or reused Copilot content maintains its protection state.

This architecture ensures Copilot does not bypass existing data protection controls, but instead amplifies them.

Oversharing Controls for Microsoft 365 Copilot

This diagram shows how SharePoint, Purview, and Copilot controls work together to reduce accidental oversharing.

Key points highlighted in the diagram:

Restricted SharePoint Search limits what Copilot can discover without changing permissions.

Sensitivity labels and DLP restrict Copilot access to sensitive content.

SharePoint Advanced Management identifies overshared or inactive sites.

Site‑level controls override broad permissions while preserving collaboration.

Oversharing controls help organisations reduce Copilot risk without redesigning permissions models.

Auditing and Retention of Copilot Usage

This diagram explains how Copilot prompts, responses, and accessed content are stored and governed.

Key points highlighted in the diagram:

Prompts and responses are stored in user mailboxes, OneDrive, or SharePoint Embedded containers.

Microsoft Purview tools provide audit, retention, and eDiscovery coverage.

Communication Compliance can detect risky or inappropriate Copilot usage.

Retention policies control how long Copilot data is preserved or deleted.

This architecture ensures Copilot interactions are auditable, discoverable, and compliant with organisational requirements.

Data Loss Prevention for Copilot

This diagram brings together classification, labeling, and DLP to show how Copilot‑related actions are evaluated.

Key points highlighted in the diagram:

Copilot responses are evaluated using existing Purview DLP policies.

Sensitive content can be blocked, audited, or warned before exposure.

Labels and DLP signals flow consistently across Copilot, Office apps, and services.

Enforcement decisions are logged for investigation and reporting.

DLP for Copilot ensures AI assistance operates within the same governance boundaries as the rest of Microsoft 365.

Using these Diagrams

Each diagram should be read as a reference flow, not a step‑by‑step implementation guide. Together, they illustrate how:

Classification generates sensitivity signals.

Sensitivity labels express protection intent, an organizational signal and consistent experience to train users on.

DLP enforces that intent consistently across endpoints, email, and collaboration services.

Protects data beyond traditional files and email.

Adapts to AI, browser, and insider risk scenarios.

Applies consistent controls across people, devices, apps, and services.

These patterns help organisations design data protection strategies that scale with modern work and AI‑assisted collaboration.

These diagrams are a team creation and maintained by the Microsoft Purview Customer Excellence Engineering team. They are downloadable in PowerPoint format here (note: link will open in PowerPoint Online + option to download) and can be used as reference and training when designing your Purview solutions deployment. For further deployment guidance, you can find our Purview Deployment blueprints here .

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