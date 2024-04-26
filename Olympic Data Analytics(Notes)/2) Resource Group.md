## What is a resource group?

A resource group is a container that enables you to manage related resources for an Azure solution. By using the resource group, you can coordinate changes to the related resources. For example, you can deploy an update to the resource group and have confidence that the resources are updated in a coordinated operation. Or, when you're finished with the solution, you can delete the resource group and know that all of the resources are deleted.

There are some important factors to consider when defining your resource group:

- All the resources in your resource group should share the same lifecycle. You deploy, update, and delete them together. If one resource, such as a server, needs to exist on a different deployment cycle it should be in another resource group.
    
- Each resource can exist in only one resource group.
    
- You can add or remove a resource to a resource group at any time.
    
- You can move a resource from one resource group to another group. For more information, see [Move resources to new resource group or subscription](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/move-resource-group-and-subscription).
    
- The resources in a resource group can be located in different regions than the resource group.
    
- When you create a resource group, you need to provide a location for that resource group.
    
    You may be wondering, "Why does a resource group need a location? And, if the resources can have different locations than the resource group, why does the resource group location matter at all?"
    
    The resource group stores metadata about the resources. When you specify a location for the resource group, you're specifying where that metadata is stored. For compliance reasons, you may need to ensure that your data is stored in a particular region.
    
    To ensure state consistency for the resource group, all [control plane operations](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/control-plane-and-data-plane) are routed through the resource group's location. When selecting a resource group location, we recommend that you select a location close to where your control operations originate. Typically, this location is the one closest to your current location. This routing requirement only applies to control plane operations for the resource group. It doesn't affect requests that are sent to your applications.
    
    If a resource group's region is temporarily unavailable, you may not be able to update resources in the resource group because the metadata is unavailable. The resources in other regions still function as expected, but you may not be able to update them. This condition may also apply to global resources like Azure DNS, Azure DNS Private Zones, Azure Traffic Manager, and Azure Front Door. You can view which types have their metadata managed by Azure Resource Manager via the [list of types for the Azure Resource Graph resources table](https://learn.microsoft.com/en-us/azure/governance/resource-graph/reference/supported-tables-resources#resources).
    
    For more information about building reliable applications, see [Designing reliable Azure applications](https://learn.microsoft.com/en-us/azure/architecture/checklist/resiliency-per-service).
    
- A resource group can be used to scope access control for administrative actions. To manage a resource group, you can assign [Azure Policies](https://learn.microsoft.com/en-us/azure/governance/policy/overview), [Azure roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal), or [resource locks](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources).
    
- You can [apply tags](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources) to a resource group. The resources in the resource group don't inherit those tags.
    
- A resource can connect to resources in other resource groups. This scenario is common when the two resources are related but don't share the same lifecycle. For example, you can have a web app that connects to a database in a different resource group.
    
- When you delete a resource group, all resources in the resource group are also deleted. For information about how Azure Resource Manager orchestrates those deletions, see [Azure Resource Manager resource group and resource deletion](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/delete-resource-group).
    
- You can deploy up to 800 instances of a resource type in each resource group. Some resource types are [exempt from the 800 instance limit](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resources-without-resource-group-limit). For more information, see [resource group limits](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#resource-group-limits).
    
- Some resources can exist outside of a resource group. These resources are deployed to the [subscription](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-to-subscription), [management group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-to-management-group), or [tenant](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-to-tenant). Only specific resource types are supported at these scopes.
    
- To create a resource group, you can use the [portal](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal#create-resource-groups), [PowerShell](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-powershell#create-resource-groups), [Azure CLI](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-cli#create-resource-groups), or an [ARM template](https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-to-subscription#resource-groups).