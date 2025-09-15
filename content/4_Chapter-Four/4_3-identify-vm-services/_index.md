---
title: "Task 3: Identify VM Information and Unsecured Services"
weight: 3
---

### Login to Linux VM Serial Console

Now that both Linux virtual machines, **linux-a-vm** and **linux-b-vm**, have been deployed, you are going to identify their assigned private and public IP (PIP) addresses, confirm which ports are open on each VM, and what access is available to and from their assigned subnets.

In the following steps 1-6, you will navigate and identify IP information for both VMs and login to each VM via the serial console, in Azure.

{{% notice tip %}}Access the serial console of each virtual machine in different browser tabs.{{% /notice %}}

1. ***Navigate*** to your Resource Group
1. ***Right Click*** on the virtual machine **linux-a-vm**
1. ***Select*** "Open Link in New Tab"

    {{< figure src="azure-identify-pip-access-1.png" alt="azure-identify-pip-access-1" >}}

    The browser tab will open to the **linux-a-vm** Overview page, under the **Essentials** and **Properties** sections, right-hand side, identify the assigned private and public IP of **linux-a-vm**

    {{< figure src="azure-identify-pip-access-2.png" alt="azure-identify-pip-access-2" >}}

1. ***Navigate*** to the bottom of the left-side menu

1. ***Expand*** "Help"

1. ***Select*** "Serial console"

1. ***Login*** to the **linux-a-vm** console using the credentials used when creating the **linux-a-vm**.

    {{< figure src="azure-identify-pip-access-3.png" alt="azure-identify-pip-access-3" >}}

1. ***Repeat*** the same process to login to the serial console of **linux-b-vm-in another tab

### The VNET security policy for company ABC is as follows

**linux-a-vm** will be the management server. Per company ABC security policy:

- **linux-a-vm** should only have SSH and PING access to **linux-b-vm**
- **linux-a-vm** should have HTTP/HTTPS access to the Internet
- **linux-a-vm** should be SSH accessible from the Internet

**linux-b-vm** is the www server.  Per company ABC security policy:

- **linux-b-vm** should be HTTP accessible from the Internet
- **linux-b-vm** should have HTTP and HTTPS access to the Internet
- **linux-b-vm** should only have PING access to **linux-a-vm**

The goals of the following steps, are to note:

- Which service ports are open and listening on each VM
- What access does each VM have across subnets
- Which services to and from the Internet are available to each VM  

Using this information, we can implement company ABC's security policies when securing the VNET with a **FortiGate**

Configure **linux-b-vm** first

{{% notice tip %}}Use the linux `clear` command to clear the screen{{% /notice %}}

1. ***Verify*** Connectivity and Services

    {{% notice note %}}These commands are completed from the **linux-b-vm**{{% /notice %}}

    - Use `ping www.yahoo.com`
      - confirms DNS and ICMP access to the Internet: (CTRL+c to stop ping)
    - Use `wget www.fortinet.com`
      - confirms port 80 access to the Internet:  (Confirm "200 OK" response)
    - Use `curl https://ipinfo.io/ip && echo " linux-b-vm's PIP"`
      - confirms port 443 access to the Internet
      - confirms Public IP assigned to **linux-b-vm**: (***Verify*** against what the Azure portal listed in the Overview section for this VM)

    {{< figure src="azure-identify-pip-access-4.png" alt="azure-identify-pip-access-4" >}}

    - ***Check*** for and install Ubuntu updates
        - `sudo apt update`
        - `sudo apt -y upgrade`
        - `clear` after updates have finished

    - ***Ping*** the private IP of **linux-a-vm**
      - `ping 192.168.1.xxx` (Refer to previous steps for Private IP)

    - ***Install*** **NMAP** Scan open ports on **linux-a-vm**
      - `sudo apt -y install nmap`
      - `nmap -F 192.168.1.xxx` (Refer to previous steps for Private IP)
      - ***Note*** the open port(s) on **linux-a-vm**

    {{< figure src="azure-identify-pip-access-5.png" alt="azure-identify-pip-access-5" >}}

    - ***Confirm*** SSH access to **linux-a-vm**:
      - `ssh azureuser@192.168.1.xxx` (Refer to previous steps for Private IP)
      - Use `sudo ss -ltn` to confirm the same open ports that NMAP reported
      - Use `exit` to disconnect from **linux-a-vm**

    {{< figure src="azure-identify-pip-access-6.png" alt="azure-identify-pip-access-6" >}}
    {{< figure src="azure-identify-pip-access-7.png" alt="azure-identify-pip-access-7" >}}

    - ***Install*** the web service **NGINX**
      - `sudo apt -y install nginx`

    {{% notice note %}}These commands are completed from the **linux-a-vm**{{% /notice %}}

    - Use `ping www.yahoo.com`
      - confirms DNS and ICMP access to the Internet: (CTRL+c to stop ping)
    - Use `wget www.fortinet.com`
      - confirms port 80 access to the Internet:  (Confirm "200 OK" response)
    - Use `curl https://ipinfo.io/ip && echo " linux-a-vm's PIP"`
      - confirms port 443 access to the Internet
      - confirms Public IP assigned to **linux-a-vm**: (***Verify*** against what the Azure portal listed in the Overview section for this VM)

    - ***Check*** for and install Ubuntu updates
        - `sudo apt update`
        - `sudo apt -y upgrade`
        - `clear` after updates have finished

    - ***Ping*** the private IP of **linux-b-vm**
      - `ping 192.168.1.xxx` (Refer to previous steps for Private IP)

    - ***Install*** **NMAP** Scan open ports on **linux-b-vm**
      - `sudo apt -y install nmap`
      - `nmap -F 192.168.1.xxx` (Refer to previous steps for Private IP)
      - ***Note*** the open port(s) on **linux-a-vm**

    - ***Confirm*** SSH access to **linux-b-vm**:
      - `ssh azureuser@192.168.1.xxx` (Refer to previous steps for Private IP)
      - Use `sudo ss -ltn` to confirm the same open ports that NMAP reported
      - Use `exit` to disconnect from **linux-b-vm**

The following diagram is a representation of your current VNET and VM deployment.

{{< figure src="azure-unsecured-vnet.png" alt="azure-unsecured-vnet" >}}
