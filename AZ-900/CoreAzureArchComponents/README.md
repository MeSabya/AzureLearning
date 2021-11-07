# Describe Core Azure Services

## Overview of Azure subscriptions, management groups, and resources
![image](https://user-images.githubusercontent.com/33947539/140633616-8c5ff752-fe84-4da4-8a95-d52052013b48.png)

- **Resources**: Resources are instances of services that you create, like virtual machines, storage, or SQL databases.

- **Resource groups**: Resources are combined into resource groups, which act as a logical container into which Azure resources like web apps, databases, and storage accounts are 
  deployed and managed.

- **Subscriptions**: A subscription groups together user accounts and the resources that have been created by those user accounts. 
  For each subscription, there are limits or quotas on the amount of resources that you can create and use. Organizations can use subscriptions to manage costs and the resources  
  that are created by users, teams, or projects.

- **Management groups**: These groups help you manage access, policy, and compliance for multiple subscriptions. All subscriptions in a management group automatically inherit the   conditions applied to the management group.


## Azure regions, availability zones, and region pairs
Azure is made up of datacenters located around the globe. When you use a service or create a resource such as a SQL database or virtual machine (VM), you're using physical equipment in one or more of these locations. These specific datacenters aren't exposed to users directly. Instead, Azure organizes them into regions. As you'll see later in this unit, some of these regions offer availability zones, which are different Azure datacenters within that region.

### Azure regions
- A region is a geographical area on the planet that contains at least one but potentially multiple datacenters that are nearby and networked together with a low-latency network. - Azure intelligently assigns and controls the resources within each region to ensure workloads are appropriately balanced.

#### Why are regions important?
-Azure has more global regions than any other cloud provider. These regions give you the flexibility to bring applications closer to your users no matter where they are. 
- Global regions provide better scalability and redundancy. 
- They also preserve data residency for your services.

### Azure availability zones
- Availability zones are physically separate datacenters within an Azure region. Each availability zone is made up of one or more datacenters equipped with independent power, 
  cooling, and networking.
- An availability zone is set up to be an isolation boundary. If one zone goes down, the other continues working. Availability zones are connected through high-speed, private   
  fiber-optic networks.
- You can use availability zones to run mission-critical applications and build high-availability into your application architecture by co-locating your compute, storage, networking, and data resources within a zone and replicating in other zones.
- **Availability zones are primarily for VMs, managed disks, load balancers, and SQL databases.***
-  Azure services that support availability zones fall into three categories:

1. **Zonal services**: You pin the resource to a specific zone (for example, VMs, managed disks, IP addresses).
2. **Zone-redundant services**: The platform replicates automatically across zones (for example, zone-redundant storage, SQL Database).
3. **Non-regional services**: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages.

### Azure region pairs
- Each Azure region is always paired with another region within the same geography (such as US, Europe, or Asia) at least 300 miles away. 
- This approach allows for the replication of resources (such as VM storage) across a geography that helps reduce the likelihood of interruptions because of events such as natural disasters, civil unrest, power outages, or physical network outages that affect both regions at once. 
- If a region in a pair was affected by a natural disaster, for instance, services would automatically failover to the other region in its region pair.

## Azure resource groups
- Resource groups are a fundamental element of the Azure platform. A **Resource group** is a logical container for resources deployed on Azure. 
- These resources are anything you create in an Azure subscription like VMs, Azure Application Gateway instances, and Azure Cosmos DB instances. 
- All resources must be in a resource group, and a resource can only be a member of a single resource group.Before any resource can be provisioned, you need a resource group for it to be placed in.
- Resource groups can't be nested.

### Azure Resource Group Example
Let's say we are developing a web application. There are several ways to do this. To keep this example simple, let's just assume we need the following 3 azure resources.

Virtual Machine - To host and run our web application
Storage Account - To store images, videos and other resources that our web application needs
SQL database - To store our application data
Let's say for this example sake we have the following environments. Most organisations have these deployment environments.
- Development
- Testing
- Staging
- PreProduction
- Production
Let's say our web application name is PragimTech.com. We might create the following 4 resource groups, one for each environment. 

rg-pragimtech-development
rg-pragimtech-staging
rg-pragimtech-preproduction
rg-pragimtech-production

you can group resources any way you want. 
- By department,
- By country,
- By application,
- By resource type or a
- Combination of these

***In general, resources that share the same deployment lifecycle are grouped, so these resources can be easily provisioned i.e created, deployed, updated, and deleted as a single unit.***

### Characterstics of resourse group:
#### Logical grouping: 
By placing resources of similar usage, type, or location in a resource group, you can provide order and organization to resources you create in Azure.
#### Life cycle:
Resource groups make it easy to remove a set of resources all at once.
#### Authorization:
Resource groups are also a scope for applying role-based access control (RBAC) permissions. By applying RBAC permissions to a resource group, you can ease administration and limit access to allow only what's needed.

## Azure Resource Manager
![image](https://user-images.githubusercontent.com/33947539/140638115-35ad0dad-7f4a-414e-a51e-c201bceead56.png)
When a user sends a request from any of the Azure tools, APIs, or SDKs, Resource Manager receives the request. 
It authenticates and authorizes the request. Resource Manager sends the request to the Azure service, which takes the requested action.

### The benefits of using Resource Manager
- Manage your infrastructure through declarative templates rather than scripts. A Resource Manager template is a JSON file that defines what you want to deploy to Azure.
- Deploy, manage, and monitor all the resources for your solution as a group, rather than handling these resources individually.
- Redeploy your solution throughout the development life cycle and have confidence your resources are deployed in a consistent state.
- Define the dependencies between resources so they're deployed in the correct order.
- Apply access control to all services because RBAC is natively integrated into the management platform.
- Apply tags to resources to logically organize all the resources in your subscription.
- Clarify your organization's billing by viewing costs for a group of resources that share the same tag.

## Azure subscriptions
- An Azure subscription is a logical unit of Azure services that links to an Azure account, which is an identity in Azure Active Directory (Azure AD) or in a directory that Azure AD trusts.
- Using Azure requires an Azure subscription. A subscription provides you with authenticated and authorized access to Azure products and services. It also allows you to provision resources. 

**There are two types of subscription boundaries that you can use:**
**Billing boundary:** This subscription type determines how an Azure account is billed for using Azure. 

**Access control boundary:** Azure applies access-management policies at the subscription level, and you can create separate subscriptions to reflect different organizational structures. An example is that within a business, you have different departments to which you apply distinct Azure subscription policies. This billing model allows you to manage and control access to the resources that users provision with specific subscriptions.

## Azure management groups
If your organization has many subscriptions, you might need a way to efficiently manage access, policies, and compliance for those subscriptions.
You organize subscriptions into containers called management groups and apply your governance conditions to the management groups. All subscriptions within a management group automatically inherit the conditions applied to the management group.


# References:
- https://www.pragimtech.com/blog/azure/azure-resource-group-benefits/
