---
title: "Task 1:  Deploy a FortiGate NVA"
weight: 4
---

In Task 1, you will deploy a FortiGate network virtual appliance (NVA) in your Resource Group.  After deployment, you will login to the FortiGate and verify settings.

### FortiGate Deployment - Prerequisite

The Single Fortinet FortiGate requires two interfaces

- external (port1) untrusted interface
- internal (port2) trusted interface

These interfaces require two additional subnets be added to VNET **acb-server-vnet**

Access **acb-server-vnet** and add these two subnets

- snet-external with address space 192.168.1.0/27
- snet-internal with address space 192.168.2.32/27

Use these screen shots for reference

{{< figure src="azure-deploy-fgt-new-subnets-1.png" alt="azure-deploy-fgt-new-subnets-1" >}}
{{< figure src="azure-deploy-fgt-new-subnets-2.png" alt="azure-deploy-fgt-new-subnets-2" >}}

### FortiGate Deployment

1. ***Navigate*** to you Resource Group
1. ***Click*** "+ Create"

    {{< figure src="azure-deploy-fgt-1.png" alt="azure-deploy-fgt-1" >}}

    You will be redirected to the Azure Marketplace.

1. ***Search*** for `Fortinet FortiGate`
1. ***Select*** "Fortinet FortiGate Next-Generation Firewall" 
1. ***Click*** "Create"
1. ***Click*** "Single VM"

    {{< figure src="azure-deploy-fgt-2.png" alt="azure-deploy-fgt-2" >}}

    You will be redirected to the **Create Single VM** template.

    Under the **Basics** tab, the **Subscription** and **Resource Groups** may already be filled in with your assigned info. If not, see the screenshot below for details.

1. Under **Instance details**, select/enter the following:

    - Region:  **West US 3**  
    - FortiGate VM instance Architecture: "X64 - Intel / AMD based processors | Gen1 VM FortiGate 6.4 - 7.4"
    - FortiGate administrative username:  `azureuser`
    - FortiGate password: `123Password#@!`
    - Confirm password:  `123Password#@!`
    - FortiGate Name Prefix:  **sgl**

1. ***Click*** "Next"

    {{< figure src="azure-deploy-fgt-3.png" alt="azure-deploy-fgt-3" >}}

1. On the **Instance** tab, select the following

    - Fortigate-VM License Type: "Pay As You Go"
    - Fortigate Image Version: "7.4.x" - **Select the latest version**

    {{% notice tip %}}Note the blue shaded areas, they are links to additional information{{% /notice %}}

1. ***Click*** "Next"

    {{< figure src="azure-deploy-fgt-4.png" alt="azure-deploy-fgt-4" >}}

1. On the **Networking** tab, select the following:

    - Virtual network:  **abc-server-vnet**
    - External Subnet:  **snet-external**
    - Internal subnet:  **snet-internal**
    - Protected subnet: **snet-a**
    - Accelerated Networking:  **Enabled**

    {{% notice note %}}snet-b will be protected as well, the template just does not have a selection for it.{{% /notice %}}

1. ***Click*** "Next"

    {{< figure src="azure-deploy-fgt-5.png" alt="azure-deploy-fgt-5" >}}

1. On the **Public IP** tab, keep the default **Public IP address** already entered.  It should have a "**(new)**" listed in the beginning of the field.

1. ***Click*** "Next"

    {{< figure src="azure-deploy-fgt-6.png" alt="azure-deploy-fgt-6" >}}

1. On the **Advanced** tab, keep the default settings.

1. ***Click*** "Review + create"

    {{< figure src="azure-deploy-fgt-7.png" alt="azure-deploy-fgt-7" >}}

1. On the **Review + create** tab, scroll down and review the template entries.

1. ***Click*** "Create"

    {{< figure src="azure-deploy-fgt-8.png" alt="azure-deploy-fgt-8" >}}

    The screen will refresh and you will see **Deployment is in progress**.

    {{< figure src="azure-deploy-fgt-9.png" alt="azure-deploy-fgt-9" >}}

    After a few minutes, you will see **Your deployment is complete**

1. ***Click*** Go to resource group

    {{< figure src="azure-deploy-fgt-10.png" alt="azure-deploy-fgt-10" >}}

1. Confirm the FortiGate NVA and its related services have been deployed.

    {{< figure src="azure-deploy-fgt-11.png" alt="azure-deploy-fgt-11" >}}

1. ***Click*** "sgl-fgt"

1. ***View*** Public IP address on overview page

    {{< figure src="azure-deploy-fgt-12.png" alt="azure-deploy-fgt-12" >}}

### FortiGate Access

1. ***Use*** the "Public IP address" in a browser to access the FortiGate interface

1. ***Enter*** the login info from above

    {{< figure src="azure-deploy-fgt-13.png" alt="azure-deploy-fgt-13" >}}

1. ***Click*** "Begin" on the **FortiGate Setup** page

    {{< figure src="azure-deploy-fgt-14.png" alt="azure-deploy-fgt-14" >}}

1. ***Click*** "Later" on the **Migrate Config with FortiConverter** page

    {{< figure src="azure-deploy-fgt-15.png" alt="azure-deploy-fgt-15" >}}

1. ***Click*** "Save and continue" on the **Automatic Patch Upgrades for v7.4** page

    {{< figure src="azure-deploy-fgt-16.png" alt="azure-deploy-fgt-16" >}}

1. ***Select*** "I acknowledge" and ***Click*** "OK" on the **Disable Automatic Patch Upgrades** page

   {{< figure src="azure-deploy-fgt-17.png" alt="azure-deploy-fgt-17" >}}

1. ***Click*** "OK" on the **Dashboard Setup** page

    {{< figure src="azure-deploy-fgt-18.png" alt="azure-deploy-fgt-18" >}}

1. ***Select*** "**Don't show again**" and ***Click*** "OK" on the **What's new in FortiOS 7.4** video

    {{< figure src="azure-deploy-fgt-19.png" alt="azure-deploy-fgt-19" >}}

The following diagram is a representation of your current VNET with Linux VM deployment and FortiGate NVA

{{< figure src="azure-deploy-fgt-20.png" alt="azure-deploy-fgt-20" >}}
