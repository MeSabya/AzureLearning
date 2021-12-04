# Create and deploy ARM templates by using the Azure portal

One of the more compelling features offered by Azure is Azure Resource Manager Templates (ARM Templates).
## Why ARM Templates

>From Microsoft’s website:
With the move to the cloud, many teams have adopted agile development methods. These teams iterate quickly. They need to repeatedly deploy their solutions to the cloud, and know their infrastructure is in a reliable state. As infrastructure has become part of the iterative process, the division between operations and development has disappeared. Teams need to manage infrastructure and application code through a unified process.

***ARM templates are a means to turn infrastructure into code.***
### What Happens when an ARM Template is run
- An ARM Template is given to the Resource Manager. 

![image](https://user-images.githubusercontent.com/33947539/144702014-cd0d8be2-12a4-4990-a719-17aea895efce.png)

>The “Azure Resource Manager” is a deployment and management service for Azure. It is a layer that allows to create update and delete resources.
Azure PowerShell provides a set of cmdlets that allows using the Azure Resource Manager
There are two implementations of Azure Powershell, the more recent Az module and the legacy AzureRM.

- The Resource Manager, in turn, converts each ARM Template into a set of, operations, it validates them, it sorts them and turns them into HTTP Calls performed against the different Resource Providers :

![image](https://user-images.githubusercontent.com/33947539/144702145-2d97eb33-3fb6-4385-a54c-9b4081de72d5.png)

### Resource Providers
![image](https://user-images.githubusercontent.com/33947539/144704447-f6a227a5-c280-4d6e-ab2d-5754b6f282bc.png)

**Resources in Azure are made available by a Resource provider, registered to the subscription. When attempting to create certain types of resources in Azure, an error may occur, preventing the resource from being created. This may happen because the Resource Provider for the type of resource that is being created has not been registered to the subscription.**

The Error will look something like this:

>The subscription [subName] does not have permissions to register the resource provider(s): [ProviderNamespace]

- Azure subscriptions come with a default set of Resource Providers to support creating various resources. For example, if you want to create a virtual machine, the 
  Microsoft.Compute Resource Provider needs to be registered to the subscription to successfully create a virtual machine.
- To create resources that use Resource Providers that are not included in the default set provided with a new subscription, will need to be registered to the subscription by a 
  user with subscription-level access, using one of the following methods:

       1. Pre-register all available or a specific Resource Provider to the subscription.
       2. Create custom role-based access control to permit registrations of Resource Providers as-needed.

[ResourceProvider in Detail](https://docs.learnondemandsystems.com/guides/cloud-slice/microsoft-azure/azure-resource-providers.md)
