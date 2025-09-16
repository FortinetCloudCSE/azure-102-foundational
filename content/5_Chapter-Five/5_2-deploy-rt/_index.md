---
title: "Task 2:  Deploy a Route Table and Create a UDR"
weight: 4
---

In Task 2, you will deploy a **Route Table** and modify the **Route Table** by associating both protected subnets to use **port2** of the FortiGate as the default route. These routes are referred to as **User Defined Routes (UDRs)**.

### Create and configure an Azure Route Table

1. ***Navigate*** to your Resource Group

1. ***Click*** "+ Create"

    {{< figure src="azure-deploy-route-table-1.png" alt="azure-deploy-route-table-1" >}}

    You will be redirected to the Azure Marketplace.

1. ***Search*** `Route Table`

1. **Select** the "Route table" offering from Microsoft

1. ***Click*** "Create"

1. ***Click*** "Route table"

    {{< figure src="azure-deploy-route-table-2.png" alt="azure-deploy-route-table-2" >}}

    You will be redirected to the **Create Route table** template.

    Under the **Basics** tab, the **Subscription** and **Resource Groups** should already be filled in with your assigned info.  If not, see the screen shot below for details.

1. Under **Instance details**, enter the following:
    - Region: **West US 3**
    - Name: `route-table`

1. ***Click*** "Review + create"

    {{< figure src="azure-deploy-route-table-3.png" alt="azure-deploy-route-table-3" >}}

1. ***Click*** "Create"

    {{< figure src="azure-deploy-route-table-4.png" alt="azure-deploy-route-table-4" >}}

1. ***Click*** on the "Resource group" when the deployment is complete

    {{< figure src="azure-deploy-route-table-5.png" alt="azure-deploy-route-table-5" >}}

1. ***Click*** on "route-table"

1. ***Click*** "Routes" under "Settings"

1. ***Click*** "+ Add"

1. ***Enter*** in the **Add route** panel

    - **Route name**:  `default`
    - **Destination type**:  Select **IP Addresses**
    - **Destination IP address/CIDR ranges**:  `0.0.0.0/0`
    - **Next hop type**: Select **Virtual appliance**
    - **Next hop address**:  `192.168.1.36`  (Confirm this is the same IP assigned to **port2** on your FortiGate NVA).

1. ***Click*** **Add**

    {{< figure src="azure-deploy-route-table-6.png" alt="azure-deploy-route-table-6" >}}
    {{< figure src="azure-deploy-route-table-7.png" alt="azure-deploy-route-table-7" >}}

    The new route called **default** is listed under the **Routes** section

    {{< figure src="azure-deploy-route-table-8.png" alt="azure-deploy-route-table-8" >}}

1. ***Add*** two more routes for **snet-a** and **snet-b**.

    - **Route name**:  `snet-a`
    - **Destination type**:  Select **IP Addresses**
    - **Destination IP address/CIDR ranges**:  `192.168.1.128/27`
    - **Next hop type**: Select **Virtual appliance**
    - **Next hop address**:  `192.168.1.36`  (Confirm this is the same IP assigned to **port2** on your FortiGate NVA).

1. ***Click*** **Add**

    - **Route name**:  `snet-b`
    - **Destination type**:  Select **IP Addresses**
    - **Destination IP address/CIDR ranges**:  `192.168.1.160/27`
    - **Next hop type**: Select **Virtual appliance**
    - **Next hop address**:  `192.168.1.36`  (Confirm this is the same IP assigned to **port2** on your FortiGate NVA).

1. ***Click*** **Add**

    {{< figure src="azure-deploy-route-table-9.png" alt="azure-deploy-route-table-9" >}}

1. ***Click*** "Subnets"

1. ***Click*** "+ Associate"

1. ***Enter*** in the **Associate subnet** panel

    - Virtual network:  **abc-server-vnet**
    - Subnet: Select **snet-a**

1. ***Click*** "OK"

1. ***Enter*** in the **Associate subnet** panel

    - Virtual network:  **abc-server-vnet**
    - Subnet: Select **snet-b**

1. ***Click*** "OK"

    {{< figure src="azure-deploy-route-table-10.png" alt="azure-deploy-route-table-10" >}}

    {{< figure src="azure-deploy-route-table-11.png" alt="azure-deploy-route-table-11" >}}

1. ***Click*** **Overview**

1. ***View*** a summary of the **Routes** and associated **Subnets**

    {{< figure src="azure-deploy-route-table-12.png" alt="azure-deploy-route-table-12" >}}

### Remove the Public IP Addresses from the Linux VMs

1. ***Navigate*** to your Resource Group

1. ***Click*** on "linux-a-vm-ip"

1. ***Click*** on "Disassociate"

1. ***Click*** "Yes" to confirm disassociation

1. ***Click*** on "Delete"

1. ***Click*** "Yes" to confirm deletion

    {{< figure src="azure-deploy-route-table-13.png" alt="azure-deploy-route-table-13" >}}
    {{< figure src="azure-deploy-route-table-14.png" alt="azure-deploy-route-table-14" >}}
    {{< figure src="azure-deploy-route-table-15.png" alt="azure-deploy-route-table-15" >}}
    {{< figure src="azure-deploy-route-table-16.png" alt="azure-deploy-route-table-16" >}}

1. ***Repeat*** for "linux-b-vm-ip"

Because the Route Table is associated to the VNET, directing traffic to the FortiGate using the Public IPs attached to the Linux VMs is not possible because traffic leaving Linux VMs will be forced to the FortiGate and there will be no awareness and the traffic will be dropped.

The following diagram is a representation of your current VNET with Linux VM deployment and FortiGate NVA

{{< figure src="azure-secured-vnet.png" alt="azure-secured-vnet" >}}
