---
title: "Task 1:  Deploy a FortiGate NVA"
weight: 4
---

In the following task, you will deploy a FortiGate network virtual appliance (NVA)in the training Resource Group that you have been assigned.  After deployment, you will login to the FortiGate and verify a few settings.

### Creation Steps

1. Navigate into your Resource Group and click on the **+ Create** located at the top left of the tool bar.

    {{< figure src="Azure-creating-vnet.PNG" alt="Azure-creating-vnet" >}}

    You will be redirected to the Azure Marketplace.

1. In the Marketplace search bar, enter **Fortinet FortiGate** and then enter.  Navigate to the **Fortinet FortiGate Next-Generation Firewall** offering from Fortinet and select **Create** and **Single VM**.

    {{< figure src="4-1-Azure-deploy-fgt-1.PNG" alt="4-1-Azure-deploy-fgt-1" >}}

    You will be redirected to the **Create Single VM** template.

1. Under the **Basics** tab, the **Subscription** and **Resource Groups** should already be filled in with your assigned info.  If not, see the screen shot below for details.

    - Under **Instance details**, select/enter the following:
        - **Region**:  "**West US 3**"  
        - **FortiGate administrative username**:  "**studentxx**"
        - **FortiGate password**/**Confirm password**:  "**FortinetAzure2024!**"
        - **Fortigate Name Prefix**:  "**studentxx**"
        - **Fortigate Image SKU**:  "**Pay As You Go**"
        - **Fortigate Image Version**: "**7.4.4**"
    - Select **Next**.

    {{< figure src="4-1-Azure-deploy-fgt-2.PNG" alt="4-1-Azure-deploy-fgt-2" >}}

1. On the **Instance** tab, review the default entries.  Note the two blue shaded areas under **FortiGate License** for future knowledge.
    - Select **Next**.

    {{< figure src="4-1-Azure-deploy-fgt-3.PNG" alt="4-1-Azure-deploy-fgt-3" >}}
    {{< figure src="4-1-Azure-deploy-fgt-4.PNG" alt="4-1-Azure-deploy-fgt-4" >}}

1. On the **Networking** tab, enter/edit the following:

    - **Virtual network**:  "**Studentxx_VNET (studentxx-azure102-rg)**".  (Do not select the option with the prepended (NEW)).
    - **External Subnet**:  "**External_Subnet**"
    - **Internal subnet**:  "**Internal_Subnet**"
    - **Protected subnet**:  "**Protected-A_Subnet**"
    - **Accelerated Networking**:  "**Enabled**"
    - Select **Next**.

    {{< figure src="4-1-Azure-deploy-fgt-5.PNG" alt="4-1-Azure-deploy-fgt-5" >}}
    {{< figure src="4-1-Azure-deploy-fgt-6.PNG" alt="4-1-Azure-deploy-fgt-6" >}}

1. On the **Public IP** tab, keep the default **Public IP address** already entered.  It should have a "**(new)**" listed in the beginning of the field.

    - Select **Next**

    {{< figure src="4-1-Azure-deploy-fgt-7.PNG" alt="4-1-Azure-deploy-fgt-7" >}}

1. On the **Advanced** tab, keep the default settings.  Note the option for the FortiGate to be managed by a FortiManager.

    - Select **Next**.
    {{< figure src="4-1-Azure-deploy-fgt-8.PNG" alt="4-1-Azure-deploy-fgt-8" >}}
    {{< figure src="4-1-Azure-deploy-fgt-9.PNG" alt="4-1-Azure-deploy-fgt-9" >}}

1. On the **Review + create** tab, scroll down and review the template entries.

    - Select **Create**.

    {{< figure src="4-1-Azure-deploy-fgt-10.PNG" alt="4-1-Azure-deploy-fgt-10" >}}

1. The screen should refresh and you will see **Deployment is in progress**.

    {{< figure src="4-1-Azure-deploy-fgt-11.PNG" alt="4-1-Azure-deploy-fgt-11" >}}

1. After a few minutes, you will see **Your deployment is complete**.  Select **Go to resource group**

    {{< figure src="4-1-Azure-deploy-fgt-12.PNG" alt="4-1-Azure-deploy-fgt-12" >}}

1. Confirm the FortiGate NVA and its related services have been deployed.

    {{< figure src="4-1-Azure-deploy-fgt-13.PNG" alt="4-1-Azure-deploy-fgt-13" >}}

1. Select **studentxx-FGT** and the Overview page will be displayed.  Look under the **Properties** tab/Networking section (mid screen, right hand column) and identify the **Public IP address** and **Private IP address**.  This information is redundant and listed in several places.  (See right hand column under **Essentials**)

    {{< figure src="4-1-Azure-deploy-fgt-14.PNG" alt="4-1-Azure-deploy-fgt-14" >}}

1. Copy and paste the **Public IP address** into your local browser and you should be directed to the FortiGate NVA login page.  Don't forget to prefix the **Public IP address** with **https://**

1. Enter the login info you created in **Step 3** above.  You will be presented with the **FortiGate Setup** page.  Click "**Begin**"

    {{< figure src="4-1-Azure-deploy-fgt-22.PNG" alt="4-1-Azure-deploy-fgt-22" >}}

1. On the **Migrate Config with FortiConverter** page, click "**Later**"

    {{< figure src="4-1-Azure-deploy-fgt-19.PNG" alt="4-1-Azure-deploy-fgt-19" >}}

1. On the **Automatic Patch Upgrades for v7.4** page, click "**Save and continue**"

    {{< figure src="4-1-Azure-deploy-fgt-20.PNG" alt="4-1-Azure-deploy-fgt-20" >}}

1. On the **Disable Automatic Patch Upgrades** page, select "**I acknowledge**" and then "**OK**"

    {{< figure src="4-1-Azure-deploy-fgt-21.PNG" alt="4-1-Azure-deploy-fgt-21" >}}

1. On the **Dashboard Setup** page, select "**OK**"

    {{< figure src="4-1-Azure-deploy-fgt-23.PNG" alt="4-1-Azure-deploy-fgt-23" >}}

1. On the **What's new in FortiOS 7.4** video, select "**Don't show again**" and "**OK**".

    {{< figure src="4-1-Azure-deploy-fgt-15.PNG" alt="4-1-Azure-deploy-fgt-15" >}}

1. Look around and get familiar with the **Dashboard/Status** page.  Note items such as the **Virtual Machine** widget with the PAYGO license, **Firmware** version, and **WAN IP**.

    {{< figure src="4-1-Azure-deploy-fgt-16.PNG" alt="4-1-Azure-deploy-fgt-16" >}}

1. Navigate on the left to **Network** and **Interfaces**.  Note the **port1** and **port2** interfaces and assigned private IP address.

    - **Why did they get assigned these subnets?**
    Note the private IP address for both **port1** and **port2**.  You will need this info for future tasks.

    {{< figure src="4-1-Azure-deploy-fgt-17.PNG" alt="4-1-Azure-deploy-fgt-17" >}}

1. Feel free to continue looking around the FortiGate GUI and see if you notice screens that are different compared to a hardware FortiGate GUI.

1. You have just deployed a **FortiGate NVA**.  The diagram below is a visual representation of your VNET with the Linux VMs and FortiGate NVA.

    {{< figure src="4-1-Azure-deploy-fgt-18.PNG" alt="4-1-Azure-deploy-fgt-18" >}}

**Continue to Chapter 5 - Task 2: Deploy a Route Table and Create a UDR**
