---
title: "Task 2: Deploy Linux Virtual Machines (VMs)"
weight: 2
---

Now that a **VNET** is configured, Task 2 will cover

- Deploying two Linux VMs in the VNET
- Identify assigned public IP (PIP)
- Confirm access to the Internet
- Confirm access between each VM

VM - **Linux-A-VM** will be assigned to the **Protected-A_Subnet**
VM - **Linux-B-VM** will be assigned to the **Protected-B_Subnet**

#### Steps to create Linux-A-VM

1. Navigate into your Resource Group and click on the **+ Create** located at the top left of the tool bar.

    ![Azure-creating-vnet](../Images/Azure-creating-vnet.PNG)  

    You will be redirected to the Azure Marketplace.

1. In the Marketplace search bar, enter **ubuntu 24.04 lts** and then enter.  Navigate to the **Ubuntu 24.04 LTS - all plans including Ubuntu Pro** offering from **Canonical** and select **Create** and **Ubuntu Server 24.04 LTS**.

    ![Azure-creating-vnet](../Images/Azure-create-linux-vm.PNG)

    You will be redirected to the **Create a virtual machine** template.

1. Under the **Basics** tab, update the following fields:

    (Leave the default entry of the other fields not listed here)
        - Resource group:  "**studentxx-azure102-rg**"
        - Virtual machine name:  "**Linux-A-VM**"
        - Availability options:  "**No infrastructure redundancy required**"
        - Security type:  "**Standard**"
        - Size:  Select "**See all sizes**"

    ![Azure-create-linux-vm-8](../Images/Azure-create-linux-vm-8.PNG)

     - On the **Select a VM size** screen, expand the **D-Series v5** section and select "**D2as_v5**" and then click **Select**

    ![Azure-create-linux-vm-9](../Images/Azure-create-linux-vm-9.PNG)

    - Continuing from the **Create a virtual machine** screen:

        - **Authentication type**:  "**Password**"
        - **Username**:  "**studentxx**"  (Replace xx with your student number)
        - **Password**:  "**FortinetAzure2024!**" (Same as your Azure portal login)
        - **Confirm password**:  "**FortinetAzure2024!**"

1. Confirm the changes and the other fields default entries match the following diagram.

    ![Azure-create-linux-vm-1](../Images/Azure-create-linux-vm-1.PNG)

    ![Azure-create-linux-vm-2](../Images/Azure-create-linux-vm-2.PNG)

    ![Azure-create-linux-vm-3](../Images/Azure-create-linux-vm-3.PNG)

1. Select **Next: Disks >**.

1. On the **Disk** tab, keep the default settings and click **Next: Networking >**.
Feel free to read through the available disk services that can be changed/enabled.

1. Under the **Networking** tab, update the following fields: (Leave the default entry of the other fields not listed here)

    - **Virtual network**:  "**Studentxx_VNET**"
    - **Subnet**:  "**Protected-A_Subnet (192.168.1.128/27)**"
    - **Public IP**:  Select **Create new**

    - On the new **Create public IP address** on the right, enter the following:
        - **Name**:  "**Linux-A-VM_PIP**"
        - **Routing preference**:  "**Internet**"
        - Select **OK**
    - **Delete public IP and NIC when VM is deleted**:  **Select**

1. Confirm the changes and the other fields default entries match the following diagram.

    ![Azure-create-linux-vm-4](../Images/Azure-create-linux-vm-4.PNG)
    ![Azure-create-linux-vm-5](../Images/Azure-create-linux-vm-5.PNG)

1. Select **Review + create >**.

1. Feel free to read through the **Management**, **Monitoring**, **Advanced**, and **Tags** tabs for additional services that can be changed/enabled.

1. Confirm the template validation has passed and select **Create**

    ![Azure-create-linux-vm-6](../Images/Azure-create-linux-vm-6.PNG)

1. The **Deployment is in progress** notice is displayed.

    ![Azure-create-linux-vm-7](../Images/Azure-create-linux-vm-7.PNG)

1. Once the **Your deployment is complete** notice is displayed, click on the **student11-azure102-rg** link to be re-directed to your resource group.

    ![Azure-create-linux-vm-10](../Images/Azure-create-linux-vm-10.PNG)

1. Verify the new **Linux-A-VM** and the associated components are listed.

    ![Azure-create-linux-vm-11](../Images/Azure-create-linux-vm-11.PNG)

#### Steps to create Linux-B-VM

1. Follow the same 1-14 steps above to create the **Linux-B-VM**. You will need to alter the following where appropriate:
            - **Virtual machine name**:  "**Linux-B-VM**"
            - **Subnet**:  "**Protected-B_Subnet (192.168.1.160/27)**"
            - **Public IP**:  Select **Create new**
        - On the new **Create public IP address** on the right, enter the following:
            - **Name**:  "**Linux-B-VM_PIP**"

1. Verify the new **Linux-B-VM** and the associated components are listed.

    ![Azure-create-linux-vm-12](../Images/Azure-create-linux-vm-12.PNG)

**Continue to Chapter 4 - Task 3: Identify VM info and Unsecured Services**
