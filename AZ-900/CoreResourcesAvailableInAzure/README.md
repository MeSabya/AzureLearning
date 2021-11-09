## What is Azure Virtual Network?
Key scenarios that you can accomplish with a virtual network include - 
- communication of Azure resources with the internet, 
- communication between Azure resources, 
- communication with on-premises resources, 
- filtering network traffic, 
- routing network traffic, and 
- integration with Azure services.

### Communicate between Azure resources
Azure resources communicate securely with each other in one of the following ways:
1. **Through a virtual network**:
2. **Through a virtual network service endpoint**:
3. **Through VNet Peering**:

### Filter network traffic:
You can filter network traffic between subnets using either or both of the following options:
1. **Network security groups**: 
Network security groups and application security groups can contain multiple inbound and outbound security rules that enable you to filter traffic to and from resources by source and destination IP address, port, and protocol.
2. **Network virtual appliances**:
performs a network function, such as a firewall, WAN optimization, or other network function.

### Route network traffic
Azure routes traffic between subnets, connected virtual networks, on-premises networks, and the Internet, by default. You can implement either or both of the following options to override the default routes Azure creates:

1. **Route tables**: You can create custom route tables with routes that control where traffic is routed to for each subnet. Learn more about route tables.
2. **Border gateway protocol (BGP) routes**: If you connect your virtual network to your on-premises network using an Azure VPN Gateway or ExpressRoute connection, you can propagate your on-premises BGP routes to your virtual networks.
