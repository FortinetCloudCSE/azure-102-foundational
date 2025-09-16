---
title: "Task 4:  Configure FortiGate Policies"
weight: 4
---

In Task 4, now that you have confirmed traffic from both Linux VMs is being routed to the FortiGate, you will create policies that will accomplish the security requirements requested by company ABC.

To meet these requirements, the following access needs to be setup for each Linux VM.

**linux-a-vm** is the management server and should have the following access:

- SSH and PING access to **linux-b-vm**
- HTTP and HTTPS access to the **Internet**
- SSH access to **linux-a-vm** from the **Internet**

**linux-b-vm** is the www server and should have the following access:

- HTTP service from the **Internet**
- HTTP and HTTPS access to the **Internet**
- PING access to **linux-a-vm**

### Configure FortiGate Policies and Objects

In the following steps, you will create

- An Address object
- A Virtual IP Address (VIP)
- A Firewall Policy for **linux-a-vm**

Then **repeat** each step to create similar configurations for **linux-b-vm**

{{% notice tip %}}In FortiGate System-->Settings change the "Idle timeout" to 60 to stay logged into the FortiGate{{% /notice %}}

From the FortiGate GUI

1. ***Navigate*** to **Policy & Objects**-->**Addresses**
1. ***Click*** "+ Create new"

    {{< figure src="azure-fgt-policy-1.png" alt="azure-fgt-policy-1" >}}

1. ***Enter*** the following:

    - **Name**:  `linux-a-vm`
    - **Interface**:  **port2**
    - **Type**:  **Subnet**
    - **IP/Netmask**:  `192.168.1.132/32`

1. ***Click*** "OK"

    {{< figure src="azure-fgt-policy-2.png" alt="azure-fgt-policy-2" >}}

1. ***Repeat*** for **linux-b-vm**.  Your **Address** screen should have both Linux VMs listed.

1. ***Click*** "+ Create new"

1. ***Enter*** the following:

    - **Name**:  `linux-b-vm`
    - **Interface**:  **port2**
    - **Type**:  **Subnet**
    - **IP/Netmask**:  `192.168.1.164/32`

1. ***Click*** "OK"

1. ***View*** the created Address Objects

    {{< figure src="azure-fgt-policy-3.png" alt="azure-fgt-policy-3" >}}

1. ***Navigate*** to **Policy & Objects**-->**Virtual IPs**
1. ***Click*** "+ Create new"

1. ***Enter*** the following:

    - Name:  `linux-a-vm_VIP`
    - Interface:  **port1**
    - External IP address/range:  `192.168.1.4`
    - Map to IPv4 address/range:  `192.168.1.132`
    - Port Forwarding:  **Enable**
    - External service port:  **22**
    - Map to IPv4 port: **22**

1. ***Click*** "OK"

    {{< figure src="azure-fgt-policy-4.png" alt="azure-fgt-policy-4" >}}

1. ***Repeat*** and create a VIP for **linux-b-vm**,  HTTP is the service port.

    - Name:  `linux-b-vm_VIP`
    - Interface:  **port1**
    - External IP address/range:  `192.168.1.4`
    - Map to IPv4 address/range:  `192.168.1.164`
    - Port Forwarding:  **Enable**
    - External service port:  **8080**
    - Map to IPv4 port: **80**

    {{< figure src="azure-fgt-policy-5.png" alt="azure-fgt-policy-5" >}}

1. ***Navigate*** to **Policy & Objects**-->**Firewall Policy**
1. ***Click*** "+ Create new"

1. ***Enter*** the following:

    - Name:  `Internet access to linux-a-vm`
    - Incoming interface:  **port1**
    - Outgoing interface:  **port2**
    - Source:  **all**
    - Destination:  **linux-a-vm_VIP**
    - Service:  **SSH**
    - NAT:  **Toggle to disabled**

1. ***Click*** "OK"

1. ***Confirm*** the new policy for **linux-a-vm** is displayed

    {{< figure src="azure-fgt-policy-6.png" alt="azure-fgt-policy-6" >}}

1. ***Enter*** the following to create a policy to allow SSH and PING access to **linux-b-vm**.

    - Name:  `SSH & PING access to linux-b-vm`
    - Incoming interface:  **port2**
    - Outgoing interface:  **port2**
    - Source:  **linux-a-vm**
    - Destination:  **linux-b-vm**
    - Service:  **SSH PING**
    - NAT:  **Toggle to disabled**

    Click **OK** and confirm the new policy is displayed.

    {{< figure src="azure-fgt-policy-7.png" alt="azure-fgt-policy-7" >}}

1. ***Repeat*** and modify to finishing adding the required policies

    **linux-a-vm** needs these additional policies

    - HTTP and HTTPS access to the **Internet**
      - Name: `linux-a-vm access to the internet`
      - NAT: **enabled**

    **linux-b-vm** needs these additional policies

    - HTTP service from the **Internet**
      - Name: `Internet access to linux-b-vm`

    - HTTP and HTTPS access to the **Internet**
      - Name: `linux-b-vm access to the internet`
      - NAT: **enabled**

    - PING access to **linux-a-vm**
      - Name: `Ping Access to linux-a-vm`

    When you are finished adding all the policies for both Linux VMs, your **Firewall Policy** page should look similar to the following:

    {{< figure src="azure-fgt-policy-8.png" alt="azure-fgt-policy-8" >}}
