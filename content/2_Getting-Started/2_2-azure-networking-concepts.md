---
title: "Azure Networking Concepts"
weight: 2
---

![](../Images/Azure-VNET-Basic.PNG)

### Azure Virtual Network
  - **Azure Virtual Network** is a service that provides the fundamental building block for your private network in Azure. An instance of the service (a virtual network) enables many types of Azure resources to securely communicate with each other, the internet, and on-premises networks. These Azure resources include virtual machines (VMs).
  - All resources in a virtual network can communicate outbound with the internet, by default. You can also use a public IP address, NAT gateway, or public load balancer to manage your outbound connections. You can communicate inbound with a resource by assigning a public IP address or a public load balancer.
  - You can connect virtual networks to each other by using **virtual peering**. The resources in either virtual network can then communicate with each other. The virtual networks that you connect can be in the same, or different, Azure regions.
  - You can connect your on-premises computers and networks to a virtual network by using any of the following options:
    - **Point-to-site virtual private network (VPN):** Established between a virtual network and a single computer in your network. Each computer that wants to establish connectivity with a virtual network must configure its connection. This connection type is useful if you're just getting started with Azure, or for developers, because it requires few or no changes to an existing network. The communication between your computer and a virtual network is sent through an encrypted tunnel over the internet.
    - **Site-to-site VPN:** Established between your on-premises VPN device and an Azure VPN gateway that's deployed in a virtual network. This connection type enables any on-premises resource that you authorize to access a virtual network. The communication between your on-premises VPN device and an Azure VPN gateway is sent through an encrypted tunnel over the internet.
    - **Azure ExpressRoute:** Established between your network and Azure, through an ExpressRoute partner. This connection is private. Traffic doesn't go over the internet.
  - You can filter network traffic between subnets by using either or both of the following options:
    - **Network security groups:** Network security groups and application security groups can contain multiple inbound and outbound security rules. These rules enable you to filter traffic to and from resources by source and destination IP address, port, and protocol.
    - **Network virtual appliances (NVA):** A network virtual appliance is a VM that performs a network function, such as a firewall or WAN optimization.  The **FortiGate** is considered a NVA.
  - Azure routes traffic between subnets, connected virtual networks, on-premises networks, and the internet, by default. You can implement either or both of the following options to override the default routes that Azure creates:
    - **Route tables:** You can create custom route tables that control where traffic is routed to for each subnet.
    - **Border gateway protocol (BGP) routes:** If you connect your virtual network to your on-premises network by using an Azure VPN gateway, ExpressRoute connection, or FortiGate NVA, you can propagate your on-premises BGP routes to your virtual networks.
 

  ### Azure Virtual Network Concepts

Before diving into the reference architecture for this workshop, let's review some basic Azure networking concepts.

- **Address space:**  When creating a virtual network, you must specify a custom private IP address space using public and private (RFC 1918) addresses. Azure assigns resources in a virtual network a private IP address from the address space that you assign. For example, if you deploy a VM in a virtual network with address space, 10.0.0.0/16, the VM is assigned a private IP like 10.0.0.4.

- **Subnets:** Subnets enable you to segment the virtual network into one or more subnetworks and allocate a portion of the virtual network's address space to each subnet. You can then deploy Azure resources in a specific subnet. Just like in a traditional network, subnets allow you to segment your virtual network address space into segments that are appropriate for the organization's internal network. Segmentation improves address allocation efficiency. You can secure resources within subnets using Network Security Groups.

- **Regions:** A virtual network is scoped to a single region/location; however, multiple virtual networks from different regions can be connected together using Virtual Network Peering.

- **Subscription:** A virtual network is scoped to a subscription. You can implement multiple virtual networks within each Azure subscription and Azure region.

In this workshop we will use these components to highlight insertion of FortiGate NGFW into an enterprise architecture. 
