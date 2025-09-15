---
title: "Task 4:  Configure FortiGate Policies"
weight: 4
---

Now that you have confirmed traffic from both Linux VMs is being routed to the FortiGate, you will create policies that will accomplish the security requirements requested by company ABC.
To meet these requirements, the following access needs to be setup for each Linux VM.

**linux-a-vm** is the management server and should have the following access:

- SSH and PING access to **linux-b-vm**
- HTTP and HTTPS access to the **Internet**
- SSH access to **linux-a-vm** from the **Internet**

**linux-b-vm** is the www server and should have the following access:

- HTTP service from the **Internet**
- HTTP and HTTPS access to the **Internet**
- PING access to **linux-a-vm**

In the following steps, you will create an address object, a VIP, and a Firewall Policy for **linux-a-vm** and then repeat each step to create similar configurations for **linux-b-vm**.

1. From the FortiGate GUI, navigate to **Policy & Objects**, **Addresses**, and click "**+ Create new**".

    {{< figure src="4-4-Azure-fgt-policy-1.PNG" alt="4-4-Azure-fgt-policy-1" >}}

1. Enter the following:

    - **Name**:  "**linux-a-vm**"
    - **Interface**:  "**port2**"
    - **Type**:  "**Subnet**"
    - **IP/Netmask**:  "**192.168.1.132/32**"

    Click **OK** and confirm the new address for **linux-a-vm** is displayed.

    {{< figure src="4-4-Azure-fgt-policy-2.PNG" alt="4-4-Azure-fgt-policy-2" >}}

1. Repeat step two above and create an address for **linux-b-vm**.  Your **Address** screen should have both Linux VMs listed.

    {{< figure src="4-4-Azure-fgt-policy-6.PNG" alt="4-4-Azure-fgt-policy-6" >}}

1. Navigate to **Policy & Objects**, **Virtual IPs**, and click "**+ Create new**".

    {{< figure src="4-4-Azure-fgt-policy-3.PNG" alt="4-4-Azure-fgt-policy-3" >}}

1. Enter the following:

    - **Name**:  "**linux-a-vm_VIP**"
    - **Interface**:  "**port1**"
    - **External IP address/range**:  "**192.168.1.4**"
    - **Map to IPv4 address/range**:  "**192.168.1.132**"
    - **Port Forwarding**:  "**Enable**"
    - **External service port**:  "**22**"
    - **Map to IPv4 port**: "**22**"

    Click **OK** and confirm the new VIP for **linux-a-vm** is displayed.

    {{< figure src="4-4-Azure-fgt-policy-4.PNG" alt="4-4-Azure-fgt-policy-4" >}}

1. Repeat step five above and create a VIP for **linux-b-vm**.  HTTP should be the service port.  Your **Virtual IPs** screen should have two entries.

    {{< figure src="4-4-Azure-fgt-policy-7.PNG" alt="4-4-Azure-fgt-policy-7" >}}

1. Navigate to **Policy & Objects**, **Firewall Policy**, and click "**+ Create new**".

    {{< figure src="4-4-Azure-fgt-policy-5.PNG" alt="4-4-Azure-fgt-policy-5" >}}

1. Enter the following:

    - **Name**:  "**Internet access to linux-a-vm**"
    - **Incoming interface**:  "**port1**"
    - **Outgoing interface**:  "**port2**"
    - **Source**:  "**all**"
    - **Destination:**:  "**linux-a-vm_VIP**"
    - **Service**:  "**SSH**"
    - **NAT**:  **Toggle to disabled**

Click **OK** and confirm the new policy for **linux-a-vm** is displayed.

    {{< figure src="4-4-Azure-fgt-policy-8.PNG" alt="4-4-Azure-fgt-policy-8" >}}
    {{< figure src="4-4-Azure-fgt-policy-9.PNG" alt="4-4-Azure-fgt-policy-9" >}}
    {{< figure src="4-4-Azure-fgt-policy-10.PNG" alt="4-4-Azure-fgt-policy-10" >}}

1. Enter the following to create a policy to allow SSH and PING access to **linux-b-vm**.

    - **Name**:  "**SSH & PING access to linux-b-vm**"
    - **Incoming interface**:  "**port2**"
    - **Outgoing interface**:  "**port2**"
    - **Source**:  "**linux-a-vm**"
    - **Destination:**:  "**linux-b-vm**"
    - **Service**:  "**SSH PING**"
    - **NAT**:  **Toggle to disabled**

    Click **OK** and confirm the new policy is displayed.

    {{< figure src="4-4-Azure-fgt-policy-11.PNG" alt="4-4-Azure-fgt-policy-11" >}}

1. Repeat and modify step nine above to finishing adding the required policies for **linux-a-vm**, HTTP and HTTPS access to the Internet, and the following policies needed for **linux-b-vm**.

    **linux-b-vm** is the www server and should have the following access:

    - HTTP service from the **Internet**
    - HTTP and HTTPS access to the **Internet**
    - PING access to **linux-a-vm**

1. When you are finished adding all the policies for both Linux-VMs, your **Firewall Policy** page should look similar to the following:

    {{< figure src="4-4-Azure-fgt-policy-12.PNG" alt="4-4-Azure-fgt-policy-12" >}}

**Continue to Chapter 5 - Task 5: Confirm Managed Traffic**
