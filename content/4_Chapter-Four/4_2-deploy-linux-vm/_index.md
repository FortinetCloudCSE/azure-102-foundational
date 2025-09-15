---
title: "Task 2: Deploy Linux Virtual Machines"
weight: 2
---

Now that a **VNET** is configured, Task 2 will cover

- Deploying two Linux Virtual Machines (VMs) in the VNET
- Identify assigned Public IP (PIP)
- Confirm access to the Internet
- Confirm access between each VM

**linux-a-vm** will have an interface in subnet **snet-a**
**linux-b-vm** will have an interface in subnet **snet-b**

#### Steps to create linux-a-vm

1. ***Click*** the Hamburger menu in the upper-left corner of the Azure Portal to show the "Portal Menu"
1. ***Click*** "Virtual machines"
1. ***Click*** "+ Create"

    {{< figure src="azure-creating-linux-vm-1.png" alt="azure-creating-linux-vm-1" >}}

    {{< figure src="azure-creating-linux-vm-2.png" alt="azure-creating-linux-vm-2" >}}

1. ***Click*** Virtual Machine", You will be redirected to the **Create a virtual machine** template.

    Under the **Basics** tab, the **Subscription** and **Resource Groups** may already be filled in with your assigned info. If not, see the screenshot below for details.

1. ***Update*** the following fields:

    (Leave the default entry for fields not listed here)
    - Resource group:  **fgtXX-azure102-workshop**
    - Virtual machine name:  `linux-a-vm`
    - Availability options:  **No infrastructure redundancy required**
    - Security type:  **Standard**
    - Image:  Select **See all images** under the image drop-down

    {{< figure src="azure-creating-linux-vm-3.png" alt="azure-creating-linux-vm-3" >}}

1. ***Enter*** `Ubuntu 24.02 LTS` in the search field
1. ***Click*** "Select"
1. ***Click*** "Ubuntu Server 24.04 LTS - x64 Gen 1"

    {{< figure src="azure-creating-linux-vm-4.png" alt="azure-creating-linux-vm-4" >}}

    {{< figure src="azure-creating-linux-vm-5.png" alt="azure-creating-linux-vm-5" >}}

    Continuing from **Create a virtual machine** Basics tab:
    - Size:  Select **See all sizes** under the size drop-down

    {{< figure src="azure-creating-linux-vm-6.png" alt="azure-creating-linux-vm-6" >}}

1. ***Search*** for `D2s_v5`
1. ***Select*** "D2s_v5"
1. ***Click*** "Select"

    {{< figure src="azure-creating-linux-vm-7.png" alt="azure-creating-linux-vm-7" >}}

    Continuing from **Create a virtual machine** Basics tab:

    - Authentication type:  **Password**
    - Username:  `azureuser`
    - Password:  `123Password#@!`
    - Confirm password:  `123Password#@!`

    {{< figure src="azure-creating-linux-vm-8.png" alt="azure-creating-linux-vm-8" >}}

1. ***Confirm*** the changes and the other field's default entries match as shown here.

    {{< figure src="azure-creating-linux-vm-9.png" alt="azure-creating-linux-vm-9" >}}

1. ***Click*** **Next: Disks >**.

    On the **Disk** tab, keep the default settings, take a moment to review the available disk services and settings.

1. ***Click*** "Next: Networking >"

    On the **Networking** tab, update the following fields:

    (Leave the default entry of the other fields not listed here)
    - Virtual network:  ***Select***   **abc-server-vnet**
    - Subnet:  ***Select*** **snet-a (192.168.1.128/27)**
    - Delete public IP and NIC when VM is deleted:  **Select**

1. ***Confirm*** the changes and the other field's default entries match as shown here.

    {{< figure src="azure-creating-linux-vm-10.png" alt="azure-creating-linux-vm-10" >}}

1. Select **Review + create >**.

    {{% notice note %}}You are skipping the **Management**, **Monitoring**, **Advanced**, and **Tags** tabs. Feel free to review those tabs to view the available services and settings on those tabs.{{% /notice %}}

1. Confirm the template validation has passed and select **Create**

    {{< figure src="azure-creating-linux-vm-11.png" alt="azure-creating-linux-vm-11" >}}

    The **Deployment is in progress** notice is displayed.

    {{< figure src="azure-creating-linux-vm-12.png" alt="azure-creating-linux-vm-12" >}}

    Once the **Your deployment is complete** notice is displayed, click on the **fgtXX-azure102-workshop** link to be re-directed to your Resource Group.

    {{< figure src="azure-creating-linux-vm-13.png" alt="azure-creating-linux-vm-13" >}}

1. Verify the new **linux-a-vm** and the associated components are listed.

    {{< figure src="azure-creating-linux-vm-14.png" alt="azure-creating-linux-vm-14" >}}

#### Steps to create linux-b-vm

1. Follow the same steps to create the **linux-b-vm**. You will need to alter the following where appropriate:

    - Virtual machine name:  `linux-b-vm`
    - Subnet:  **snet-b (192.168.1.160/27)**

1. Verify the new **linux-b-vm** and the associated components are listed.

    {{< figure src="azure-creating-linux-vm-15.png" alt="azure-creating-linux-vm-15" >}}
