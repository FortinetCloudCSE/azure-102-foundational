---
title: "Task 5:  Confirm Managed Traffic"
weight: 4
---

In Task five, you will confirm that the **Firewall Policies** are correct and accomplish the security requirements for Company ABC.  In the following steps, you will run the same cli commands on each Linux VM to confirm which services are reachable and blocked.

**Summary of access to/from each Linux VM:**

**linux-a-vm** is the management server and should have the following access:

- SSH and PING access to **linux-b-vm**
- HTTP and HTTPS access to the **Internet**
- SSH access to **linux-a-vm** from the **Internet**

    From the **linux-a-vm** CLI:

    1. Ping the private IP of **linux-b-vm** and confirm replies.

    1. Confirm SSH access to **linux-b-vm** and login:  `**ssh studentxx@192.168.1.xxx**`
        - Type **exit** to disconnect from **linux-b-vm**.

    1. Confirm port 80 access to the Internet:  `**wget www.fortinet.com**`

    1. Confirm port 443 access to the Internet and the public IP assigned to **linux-a-vm**: `**curl https://ipinfo.io/ip**` Confirm against what the Azure portal has listed  as the Public IP assigned to the FortiGate or confirm against the IP you used to login to the FortiGate GUI.

    1. From your client of choice, SSH from the Internet to the VIP assigned to **linux-a-vm**.  If you do not have a SSH client installed, use the following website and scan for the SSH service - <https://dnschecker.org/port-scanner.php>.  Select **Port Type**:  "**Server Ports**".

    Why is HTTPS showing up on the scan results?

**linux-b-vm** is the www server and should have the following access:

- HTTP and HTTPS access to the **Internet**
- PING access to **linux-a-vm**
- HTTP service available from the **Internet**

    From the **linux-b-vm** CLI:

    1. Confirm port 80 access to the Internet:  `**wget www.fortinet.com**`

    1. Confirm port 443 access to the Internet and the public IP assigned to **linux-b-vm**: `**curl https://ipinfo.io/ip**` (Confirm against what the Azure portal has listed  as the Public IP assigned to the FortiGate or confirm against the IP you used to login to the FortiGate GUI.)

    1. Ping the private IP of **linux-a-vm** and confirm replies.

    1. From your local browser, open a tab and enter `**http://x.x.x.x**`  (x.x.x.x is the VIP of **linux-b-vm**)  Confirm you get an NGINX welcome screen.

Congrats if you confirmed access on all the requirements above on the first check.

If time permits try enabling other ports on the Linux VMs and allowing access via the FortiGate.
Also, spend some time looking around the FortiGate NVA GUI and see if you notice differences between what options are available compared to the FortiGate hardware GUI.

Thank you for attending Azure 102 Foundational FortiGate
