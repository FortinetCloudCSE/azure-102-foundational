---
title: "Task 5:  Confirm Managed Traffic"
weight: 4
---

In Task 5, you will confirm that the **Firewall Policies** are correct and accomplish the security requirements for Company ABC.  In the following steps, you will run the same cli commands on each Linux VM to confirm which services are reachable and blocked.

**Summary of access to/from each Linux VM:**

**linux-a-vm** is the management server and should have the following access:

- SSH and PING access to **linux-b-vm**
- HTTP and HTTPS access to the **Internet**
- SSH access to **linux-a-vm** from the **Internet**

    From the **linux-a-vm** CLI:

    1. `ping 192.168.1.164`  <-- Most likely the Private IP of **linux-b-vm**
        - Ping the private IP of **linux-b-vm** and confirm replies

    1. `ssh azureuser@192.168.1.164` <-- Most likely the Private IP of **linux-b-vm**
        - Confirm SSH access to **linux-b-vm** and login
        - Type **exit** to disconnect from **linux-b-vm**

    1. `wget www.fortinet.com`
        - Confirm port 80 access to the Internet

    1. `curl https://ipinfo.io/ip`
        - Confirm port 443 access to the Internet and the public IP assigned to **linux-a-vm**
        - Confirm against what the Azure portal has listed as the Public IP assigned to the FortiGate

    1. `ssh azureuser@<public-ip-of-fortigate>`
        - From your client of choice, SSH from the Internet to the VIP assigned to **linux-a-vm**
        - If you do not have a SSH client installed, use the following website and scan for the [SSH service](https://dnschecker.org/port-scanner.php).
            - Select **Port Type**:  "**Server Ports**"

**linux-b-vm** is the www server and should have the following access:

- HTTP and HTTPS access to the **Internet**
- PING access to **linux-a-vm**
- HTTP service available from the **Internet**

    From the **linux-b-vm** CLI:

    1. `ping 192.168.1.132`  <-- Most likely the Private IP of **linux-a-vm**
        - Ping the private IP of **linux-a-vm** and confirm replies

    1. `wget www.fortinet.com`
        - Confirm port 80 access to the Internet

    1. `curl https://ipinfo.io/ip`
        - Confirm port 443 access to the Internet and the public IP assigned to **linux-b-vm**
        - Confirm against what the Azure portal has listed as the Public IP assigned to the FortiGate

    1. From your local browser, open a tab and enter `http://x.x.x.x:8080`
      - x.x.x.x is the Public IP of the FortiGate
      - Confirm the display of NGINX welcome screen.

If all the tests worked as expected you have successfully deployed workloads in an Azure environment and secured them with Fortinet FortiGate.

Thank you for attending Azure 102 Foundational - FortiGate
