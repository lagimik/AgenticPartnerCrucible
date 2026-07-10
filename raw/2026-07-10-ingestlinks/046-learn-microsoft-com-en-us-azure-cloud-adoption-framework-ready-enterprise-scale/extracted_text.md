This browser is no longer supported.

Upgrade to Microsoft Edge to take advantage of the latest features, security updates, and technical support.

Access to this page requires authorization. You can try signing in or changing directories .

Access to this page requires authorization. You can try changing directories .

Transition an existing Azure environment to the Azure landing zone reference architecture

Many organizations have an existing Azure footprint, one or more subscriptions, and potentially an existing management group structure. Depending on their business requirements and scenarios, they might have Azure resources deployed, such as Azure VPN Gateway or Azure ExpressRoute for hybrid connectivity.

This article provides recommendations to help your organization navigate changes based on your existing Azure environment that's transitioning into the Azure landing zone reference architecture. This article also describes considerations for moving resources in Azure, for example moving a subscription from one existing management group to another management group. Consider these recommendations to help you evaluate and plan the transition of your existing Azure environment.

Move resources in Azure

You can move some resources in Azure after creation. There are different approaches that are subject to a user's Azure role-based access control (RBAC) permissions at and across scopes. The following table outlines which resources you can move, at which scope, and the pros and cons associated with each resource.

To determine which move strategy you should use, consider the following examples.

Typically, you move subscriptions to organize them into management groups or to transfer subscriptions to a new Microsoft Entra ID tenant. Moving a subscription to a new tenant is mainly for transferring billing ownership . For more information about how to move subscriptions across management groups in the same tenant, see Moving management groups and subscriptions .

Azure RBAC requirements

To assess a subscription prior to a move, it's important that the user has the appropriate Azure RBAC. The user might be an owner on the subscription (direct role assignment) and have write permission on the target management group. Built-in roles that support write permission on the target management group are the owner role, the contributor role, and the management group contributor role.

If the user has an inherited owner role permission on the subscription from an existing management group, you can only move the subscription to the management group in which the user is assigned the owner role.

Existing subscriptions might be subject to Azure policies that are assigned directly or assigned at the management group where they're currently located. It's important to assess current policies and the policies that might exist in the new management group or the management group hierarchy.

You can use Azure Resource Graph to perform an inventory of existing resources and compare their configuration with the policies that exist at the destination.

After you move subscriptions to a management group with existing Azure RBAC and policies in place, consider the following factors:

For any Azure RBAC that's inherited to the moved subscriptions, the user tokens in the management group cache might take up to 30 minutes to refresh. To expedite this process, you can refresh the token by signing out and in, or request a new token.

For any Azure RBAC that's inherited to the moved subscriptions, the user tokens in the management group cache might take up to 30 minutes to refresh. To expedite this process, you can refresh the token by signing out and in, or request a new token.

A policy in which the assignment scope includes the moved subscriptions performs an audit only on the existing resources. An existing resource in the subscription that's subject to a: DeployIfNotExists policy effect appears as noncompliant and isn't automatically remediated. A user must manually perform the remediation. Deny policy effect appears as noncompliant and isn't rejected. A user must manually mitigate this result as appropriate. Append and Modify policy effect appears as noncompliant and requires a user to mitigate. Audit and AuditIfNotExist policy effect appears as noncompliant and requires a user to mitigate.

A policy in which the assignment scope includes the moved subscriptions performs an audit only on the existing resources. An existing resource in the subscription that's subject to a:

DeployIfNotExists policy effect appears as noncompliant and isn't automatically remediated. A user must manually perform the remediation.

DeployIfNotExists policy effect appears as noncompliant and isn't automatically remediated. A user must manually perform the remediation.

Deny policy effect appears as noncompliant and isn't rejected. A user must manually mitigate this result as appropriate.

Deny policy effect appears as noncompliant and isn't rejected. A user must manually mitigate this result as appropriate.

Append and Modify policy effect appears as noncompliant and requires a user to mitigate.

Append and Modify policy effect appears as noncompliant and requires a user to mitigate.

Audit and AuditIfNotExist policy effect appears as noncompliant and requires a user to mitigate.

Audit and AuditIfNotExist policy effect appears as noncompliant and requires a user to mitigate.

All new writes to resources in the moved subscription are subject to the assigned policies in real time like normal.

All new writes to resources in the moved subscription are subject to the assigned policies in real time like normal.

Typically, you move resources when you want to consolidate resources into the same resource group if they share the same lifecycle. Or if you want to move resources to a different subscription due to cost, ownership, or Azure RBAC requirements.

When you move resources, the source resource group and the target resource group are locked during the move operation. You can't add, update, or delete resources in the resource groups. A resource move operation doesn't change the location of the resources.

For more information about how to move resources across resource groups and subscriptions in the same tenant, see Move resources to a new resource group or subscription .

To minimize the effect of regional outages, we recommend that you place resources in the same region as the resource group. For more information, see Resource group location alignment .

If you have resources in different regions within the same resource group, consider moving your resources to a new resource group or subscription .

To determine if your resource supports moving to another resource group , inventory your resources by cross-referencing them. Ensure that you meet the appropriate prerequisites .

Before you move resources

Prior to a move operation, you must verify that the resources are supported , and assess their requirements and dependencies. For example, when you move a peered virtual network, you have to disable virtual network peering first, and re-enable peering after the move operation finishes. Plan in advance for the disable and re-enable dependency so you understand the effect on existing workloads that might be connected to your virtual networks.

After you move resources

When you move the resources into a new resource group in the same subscription, any inherited Azure RBAC and policies from the management group or subscription still apply. This also applies if you move to a resource group in a new subscription where the subscription might be subject to other Azure RBAC and policy assignment. You have to validate the resource compliance and access controls.

The following scenarios describe how to migrate and transition an existing environment into the Azure landing zone reference architecture.

Alignment scenarios Transition a single subscription with no management groups to the Azure landing zone reference architecture Transition management groups to the Azure landing zone reference architecture Transition a regional organization to the Azure landing zone reference architecture

Transition a single subscription with no management groups to the Azure landing zone reference architecture

Transition management groups to the Azure landing zone reference architecture

Transition a regional organization to the Azure landing zone reference architecture

Alignment approaches Transition an environment by duplicating a landing zone management group (Recommended)

Alignment approaches

Transition an environment by duplicating a landing zone management group (Recommended)

Journey toward the target architecture

Was this page helpful?

Need help with this topic?

Want to try using Ask Learn to clarify or guide you through this topic?

Additional resources

Last updated on 2025-12-19

Was this page helpful?

Need help with this topic?

Want to try using Ask Learn to clarify or guide you through this topic?

Consumer Health Privacy