---
title: "Task 1: Deploy an Azure Virtual Network (VNET)"
weight: 1
---

Deploy a VNET (Virtual Network) in the assigned workshop **Resource Group**.

1. ***Click*** the Hamburger menu in the upper-left corner of the Azure Portal to show the "Portal Menu"
1. ***Click*** "Virtual networks"
1. ***Click*** "+ Create"

    {{< figure src="azure-portal-menu.png" alt="azure-portal-menu" >}}

    {{< figure src="azure-creating-vnet-1.png" alt="azure-creating-vnet-1" >}}

    {{< figure src="azure-creating-vnet-2.png" alt="azure-creating-vnet-2" >}}

    You will be redirected to the **Create virtual network** template.

    Under the **Basics** tab, the **Subscription** and **Resource Groups** may already be filled in with your assigned info. If not, see the screenshot below for details.

1. In the **Instance details** section, enter the following:

    - Virtual network name: `abc-server-vnet`
    - Region: **(US) West US 3**

1. ***Click*** "Next : Security"

    {{< figure src="azure-creating-vnet-3.png" alt="azure-creating-vnet-3" >}}

1. On the **Security** tab, ensure **none** of the services are selected - Feel free to read through the available services that can be enabled.

1. ***Click*** "Next : IP addresses"

1. ***Edit*** the default address space, change to `192.168.1.0/24`

1. ***Click*** The pencil icon to the right of the "default" subnet, in the new window to the right, update the following settings:  

    - Name:  `snet-a`
    - Starting address: `192.168.1.128`
    - Size: **/27**
    - Click **Save**

    {{< figure src="azure-creating-vnet-4.png" alt="azure-creating-vnet-4" >}}

1. ***Click*** "+ Add a subnet" add the following subnet:

    - Name:  `snet-b`
    - Starting address: `192.168.1.160`
    - Size: **/27**
    - Click **Add**

    {{< figure src="azure-creating-vnet-5.png" alt="azure-creating-vnet-5" >}}

1. ***Click*** "Review + create"

    {{< figure src="azure-creating-vnet-6.png" alt="azure-creating-vnet-6" >}}

1. ***Confirm*** the settings

1. ***Click*** "Create"

    {{< figure src="azure-creating-vnet-7.png" alt="azure-creating-vnet-7" >}}

1. ***Click*** your Resource Group link, When the deployment is complete

    {{< figure src="azure-creating-vnet-8.png" alt="azure-creating-vnet-8" >}}

Your Resource Group should now have a VNET named **abc-server-vnet**

{{< figure src="azure-creating-vnet-9.png" alt="azure-creating-vnet-9" >}}

1. ***Click*** on the VNET name and explore the various settings that can be applied to or utilized with an Azure Virtual Network.

1. ***Click*** on "Subnets" under "Settings" to view the subnets that were just created.

{{< figure src="azure-creating-vnet-10.png" alt="azure-creating-vnet-10" >}}

{{< figure src="azure-creating-vnet-11.png" alt="azure-creating-vnet-11" >}}

At this point these are your Azure Resources

{{< figure src="azure-vnet-basic.png" alt="azure-vnet-basic" >}}
