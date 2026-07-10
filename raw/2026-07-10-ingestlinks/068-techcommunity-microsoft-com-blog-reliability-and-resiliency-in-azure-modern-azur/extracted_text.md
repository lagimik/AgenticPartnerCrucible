Microsoft Community Hub

Communities Products

Reliability and Resiliency in Azure

Modern Azure Resilience with Mark Russinovich

Choosing the Right Multi-Region Resilience Pattern

Resiliency in the cloud reflects different priorities from consistent performance, to withstanding failures, to predictable recovery. These map to reliability, resiliency, and recoverability, which together guide how workloads should be designed on Azure. This post extends foundational guidance with practical multi‑region design decisions, including when to use availability zones, paired regions, and non‑paired regions to meet business continuity goals.

Reliability in Azure isn’t defined by a single recommendation, but by a set of architectural patterns designed to balance cost, complexity, recovery speed, and operational effort—because no single approach fits every workload. While disaster recovery is a common driver for multi‑region designs, long‑term scale planning also matters. Azure regions operate within defined physical and latency boundaries, and large-scale workloads may eventually approach the practical capacity limits of a single region.

This post introduces four resilience patterns, outlining when and why to use each so you can assess options based on your non‑functional requirements. It also explains how availability zone–based designs can often provide an alternative to paired regions as a default choice.

Here are a few common reliability and availability architecture patterns:

In-region High Availability (HA) with Availability Zones (AZ) : Maximize availability within a single Azure region by deploying across multiple availability zones .

Regional Business Continuity and Disaster Recovery (BCDR) : A primary/secondary region strategy implemented across separate Azure regions, selected based on geographic risk boundaries, regulatory requirements, and service availability. Recovery sequencing and failover behaviors are defined by workload dependencies and organizational requirements.

Non-paired region BCDR : A primary/secondary region strategy where the secondary region is chosen based on requirements such as capacity, service availability, data residency, and network latency. This approach also supports long‑term scale planning, since Azure regions operate within physical datacenter footprints and latency boundaries and can reach practical capacity limits as workloads grow. See multi‑region solutions in non‑paired regions .

Multi-region active/active : Deploy workloads across multiple regions simultaneously so that each region can serve production traffic. This approach can provide both high availability and disaster resilience while improving global performance, but it introduces additional architectural complexity and operational overhead.

The rest of this post helps you understand the tradeoffs across these patterns, enabling you to select the right approach per workload while avoiding unnecessary cost and operational complexity.

First post in this series: Achieve agility and scale in a dynamic cloud world

Why did Azure launch with paired regions?

Launched in 2010, but rebranded to Microsoft Azure in 2014, the regions were introduced in pairs (West US & East US, West Europe & North Europe, Southeast Asia & East Asia) to align with common enterprise business continuity practices at the time. Many organizations operated multiple datacenters within the same geographic boundary, separated by sufficient distance to reduce shared risk while maintaining regulatory and operational alignment. This design mirrored familiar enterprise BCDR practices at the time and offered:

A familiar primary/secondary failover pattern consistent with enterprise BCDR strategies

A familiar primary/secondary failover pattern consistent with enterprise BCDR strategies

Support for regulatory or data residency requirements that required disaster recovery within a defined geographic boundary

Turnkey replication capabilities for services such as Geo-Redundant Storage (GRS)

Platform-level sequencing of updates to reduce the likelihood of simultaneous regional impact

Platform-level sequencing of updates to reduce the likelihood of simultaneous regional impact

A defined regional recovery prioritization model for rare geography-wide incidents

A defined regional recovery prioritization model for rare geography-wide incidents

This model provided assurance that Azure could meet or exceed the resilience of legacy enterprise environments while simplifying early cloud adoption through predefined recovery patterns.

However, Azure’s engineering strategy has evolved. Many services now support replication to a region of choice rather than being limited to predefined pairs. This provides architects with greater flexibility to select regions based on workload requirements, risk boundaries, compliance constraints, capacity considerations, and cost models.

It’s important to recognize that regional parity is never guaranteed even between paired regions. Differences in service availability, supported SKUs, scale limits, capacity, cost and operational maturity must be explicitly accounted for in the workload design.

How has cloud resilience evolved since launch?

The introduction of Availability Zones in 2018 provides a significant advancement in Azure resilience. Availability Zones are physically isolated groups of data centers within a region; each zone has independent power, cooling and networking. Many Azure services (App Service, Storage, Azure SQL etc.) use zones to provide platform-managed resilience. In addition, customers can deploy zonal resources, such as virtual machines, into specific zones or distribute them across zones to design for higher availability.

Where previously Azure regions were launched in pairs, since 2020, regions have been typically designed with multiple availability zones, without a paired region. This design enables:

High availability within a single region

Platform-managed resilience for most failure scenarios

Reduced need for multi-region deployments for standard high-availability requirements

How should customers design for resilience when using both paired and non-paired regions?

To decide which resiliency model makes sense, customers should start by defining clear expectations including uptime targets, recovery time objectives (RTO), recovery point objectives (RPO), latency tolerance, and data residency. These non-functional requirements should directly influence architectural decisions.

In practice, High Availability (HA) and Disaster Recovery (DR) are differentiated by recovery objectives rather than geography. HA architectures target near-zero downtime and minimal data loss, while DR solutions allow for defined recovery time and acceptable data loss.

While HA is commonly established within a region using availability zones, it can also be achieved across regions through active-active designs. Similarly, DR is typically implemented across regions using replication and failover strategies.

When designing high availability within a region, Azure builds on AZs with 2 models:

Zone-redundant resources are replicated across multiple availability zones to ensure data remains accessible even if one zone fails. Some services provide built-in zone redundancy, while others require manual configuration. Typically, Microsoft chooses the zones used for your resources, though some services allow you to select them.

Zonal resources are deployed in a single availability zone and do not provide automatic resiliency against zone outages. While faults in other zones do not affect them, ensuring resiliency requires deploying separate resources across multiple zones. Microsoft does not handle this process; you are responsible for managing failover if an outage occurs.

The decision to design a zone-resilient architecture is critical for balancing availability requirements with cost and regional capacity constraints. Designing workloads to be resilient across availability zones is generally the preferred approach for improving availability and protecting against zone-level failures. Deploying workloads across availability zones can enhance fault tolerance and reduce downtime when supported by the Azure service being used. However, architects should still consider workload characteristics, cost implications, and potential latency impacts, which may vary depending on the services and architecture patterns involved.

Ultimately, zone resiliency is an architectural decision that should be strategically aligned with business priorities and risk tolerance, not simply treated as a checkbox to be ticked during deployment.

Region pairs should be viewed as an architectural choice rather than a rule. Historically, paired regions played a key role in minimizing correlated failures and streamlining platform updates and recovery processes. However, as the Azure Safe Deployment Practices (SDP) have matured, the advantages of region pairs have become more nuanced. Over time, SDP has evolved to support safer and more flexible change management through longer and more adaptable bake times, richer operational signal integration, and an expanded understanding of regional deployment boundaries. These improvements enable Azure to release changes more safely across a growing and increasingly diverse regional footprint, while still balancing reliability with time‑to‑market. As a result, regional pairs are no longer the sole mechanism for managing correlated change risk, but one of several architectural tools customers can apply based on their resiliency and compliance needs.

Using non-paired regions or a mix of paired and non-paired regions allows customers to design high availability and disaster recovery architectures that are driven by business, compliance, and application requirements rather than fixed regional relationships. This enables customers to optimize data residency, regulatory boundaries, latency to specific user populations, and provide differentiated recovery objectives across their workloads. This approach can also reduce exposure to rare but high-impact platform-level events by avoiding tightly coupled regional behaviors.

While some Azure services natively simplify replication and recovery within paired regions, and others support replication across arbitrary regions (such as Azure SQL, Cosmos DB, and Azure Blob Storage with object replication), non-paired designs encourage explicit, workload-aware resiliency strategies such as application-level replication, asynchronous data sync, and failover orchestration. Although this introduces more architectural responsibility and may require compensating for paired region features, it delivers greater transparency, predictable recovery behavior, and alignment with business-driven RTO/RPO requirements rather than platform defaults. Regional failover is a customer‑orchestrated decision; customers should design, test, and operate their own failover and failback processes rather than assuming platform‑initiated regional failover.

Designing for regional resilience requires distinguishing between workload mobility and data protection. Azure provides two complementary capabilities that address these needs differently: Azure Site Recovery (ASR) and Azure Backup.

Azure Site Recovery (ASR) enables near‑continuous replication and orchestrated failover of virtual machine–based workloads to a region of choice, not limited to paired regions. ASR is the primary mechanism for customers who need low RPO, controlled failover, and workload restart in a secondary region. This is especially relevant for regions without a paired region or where the paired region does not meet capacity, service availability, or compliance needs.

Azure Backup provides durable, policy‑based data protection, independent of compute availability. While Azure Backup is not a high‑availability or infrastructure failover solution, it plays a critical role when services do not support region‑of‑choice replication natively. In these scenarios, backup and restore become the recovery mechanism.

These two services are often used together: ASR for VM‑level workload continuity, and Azure Backup for protecting and restoring data across regions, including to non‑paired regions.

I am using paired regions today – does this mean I need to change my architecture?

If your current architecture is built around paired regions for compliance, data residency, or strict disaster recovery objectives, that model stays valid and supported. Azure continues to support paired regions providing prioritized recovery sequencing, staggered platform updates, and geo-aligned data residency, all backed by Microsoft’s global infrastructure strategy.

What has changed is that paired regions are no longer the only way to achieve enterprise-grade resilience. For many workloads that adopted a paired region (1+1) model primarily to protect against local datacenter failure, Availability Zones combined with geo-redundant services now provide equivalent or better protection with far less architectural complexity and cost. The shift to nonpaired regions is therefore not a forced migration, but an opportunity to simplify. Customers can continue using paired regions where business requirements demand it, while selectively modernizing other workloads to take advantage of platform-managed zone resilience.

What’s coming up next for resilience in Azure?

Resilience is evolving from static guidance to continuous, workload-aware execution. A multi-region strategy isn’t only about recovery; it’s also a practical hedge against regional capacity constraints (regions have physical limits within a latency boundary, so growth can eventually hit caps).

Resiliency agent in Azure Copilot (preview) helps you spot missing resiliency coverage—such as zone alignment gaps or missing backup/DR—and provides automated guidance (including scripts) to remediate issues, configure Azure Backup and Azure Site Recovery, and define recovery drills.

Resiliency in Azure brings zone resiliency, high availability, backup, DR, and ransomware protection together into a unified experience within Azure Copilot, enabling teams to set resiliency goals, receive proactive recommendations, and view service‑group insights via Azure portal.

If you’re looking for service-specific BCDR and replication guidance, use these authoritative starting points:

Cloud Adoption Framework (CAF) – Landing zone design area (BCDR) : guidance to define platform DR requirements (RTO/RPO), data residency considerations, and operational readiness as part of landing zone design.

Azure Well-Architected Framework (WAF) – Disaster recovery strategies : guidance for structuring, testing, and operating DR plans aligned to recovery targets, with links to companion DR planning resources.

WAF design guide – Regions & Availability Zones : how to choose between zone- vs region-based approaches and understand reliability/cost/performance tradeoffs.

Azure service reliability guides : service-by-service reliability/replication behavior and customer responsibilities.

Non‑paired multi‑region configurations : examples of supported multi-region approaches when regions aren’t paired.

Validate feasibility before you design : confirm service/SKU/zone availability in both regions.

Next step : Explore Azure Essentials for guidance and tools to build secure, resilient, cost-efficient Azure projects. To see how shared responsibility and Azure Essentials come together in practice, read Resiliency in the cloud—empowered by shared responsibility and Azure Essentials and How to design reliable, resilient, and recoverable workloads on Azure on the Microsoft Azure Blog.

For expert-led, outcome-based engagements to strengthen resiliency and operational readiness, Microsoft Unified provides end-to-end support across the Microsoft cloud. To move from guidance to execution, start your project with experts and investments through Azure Accelerate .

Architecture strategies for using Availability Zones and Region

Architecture strategies for highly available multi-region design

Architecture strategies for designing a Disaster Recovery strategy

Multi-Region solutions in nonpaired Regions

Develop a disaster recovery plan for multi-region deployments

Azure Regions and Services

Azure region pairs and nonpaired regions

Reliability guides for Azure services

Reliability guides for Azure services

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