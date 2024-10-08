---
title: "Task 1: Deploy an Azure Virtual Network (VNET)"
weight: 1
---





In task one, you will deploy VNET (Virtual Network) in the training **Resource Group** that you have been assigned to.


- 1. Navigate into your Resource Group and click on the **+ Create** located at the top left of the tool bar.
![](../Images/Azure-creating-vnet.PNG)  

You will be redirected to the Azure Marketplace.

- 2. In the Marketplace search bar, enter **Virtual Network** and then enter.  Navigate to the **Virtual Network** offering from Microsoft and select **Create** and **Virtual network**.
![](../Images/Azure-creating-vnet-1.PNG)


You will be redirected to the **Create virtual network** template.

- 3. Under the **Basics** tab, the **Subscription** and **Resource Groups** should already be filled in with your assigned info.  If not, see the screen shot below for details.
    - Under **Instance details**, enter the following:
        - **Virtual network name**: "**Studentxx_VNET**" (Replace "**xx**" with your assigned student number)
        - **Region**: "**(US) West US 3**"

    - Select **Next**.
![](../Images/Azure-creating-vnet-2.PNG)


- 4. On the **Security** tab, make sure none of the services are selected and click **Next**.
Feel free to read through the available services that can be enabled.

- 5. On the **IP address** tab, edit the default address space to "**192.168.1.0/24**".
- Select the edit button (Red) next to the "default" subnet and, in the new window to the right, update the following info:  
    - **Name**:  "**External_Subnet**"
    - **Starting address**:  "**192.168.1.0**"
    - **Size**: "**/27**"
- Select **Save** 
![](../Images/Azure-creating-vnet-3.PNG)

- Select **+ Add a subnet** (see red below), and add the following info:
    - **Name**:  "**Internal_Subnet**"
    - **Starting address**:  "**192.168.1.32**"
    - **Size**:  "**/27**"
    - Select **Add**
![](../Images/Azure-creating-vnet-4.PNG)


- 6. Continue to **+ Add a subnet** for "**Protected-A_Subnet**" and "**Protected-B_Subnet**" with their respective subnets.  See the diagram below for **IP address range** assignments.  Select **Next**.
![](../Images/Azure-creating-vnet-5.PNG)


- 7. On the **Tags** tab, select **Next**.  Nothing to enter here.

- 8. On the **Review + create** tab, confirm the template summary and select **create**.
![](../Images/Azure-creating-vnet-6.PNG)

- 9. When the deployment is complete, you will get a **Your deployement is complete** notice.
    - Confirm your deployment has completed and under **Resource group** select the "**studentxx-azure102-rg**" link.  See red section below.
![](../Images/Azure-creating-vnet-7.PNG)

- 10. Your screen should return you to your respective resource group with the new virtual network listed.  Feel free to click on the new virtual network and look around.
![](../Images/Azure-creating-vnet-8.PNG)


- 11. You have just created an **Azure virtual network (VNET)**.  The diagram below is a visual representation of your new VNET.
![](../Images/Azure-VNET-Basic.PNG)

**Continue to **Chapter 4 - Task 2: Deploy Linux Virtual Machines (VMs)**.**



