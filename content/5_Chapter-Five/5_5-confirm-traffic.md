---
title: "Task 5:  Confirm Managed Traffic"
weight: 4
---





In Task five, you will confirm that the **Firewall Policies** are correct and accomplish the security requrements for Company ABC.  In the following steps, you will run the same cli commands on each Linux VM to confirm which services are reachable and blocked.

**Summary of access to/from each Linux VM:**

**Linux-A-VM** is the management server and should have the following access:
- SSH and PING access to **Linux-B-VM**
- HTTP and HTTPS access to the Internet
- SSH access to **Linux-A-VM** from the Internet

- 1. From the **Linux-A-VM** CLI:
        - Ping the private IP of **Linux-B-VM** and confirm replies. 
        - Confirm SSH access to **Linux-B-VM** and login:  **ssh studentxx@192.168.1.xxx**"
            - Type **exit** to disconnect from **Linux-B-VM**.
        - Confirm port 80 access to the Internet:  "**wget www.fortinet.com**"
        - Confirm port 443 access to the Internet and the public IP assigned to **Linux-A-VM**: "**curl https://ipinfo.io/ip**"  (Confirm against what the Azure portal has listed  as the Public IP assigned to the FortiGate or confirm against the IP you used to login to the FortiGate GUI.
        - From your client of choice, SSH from the Internet to the VIP assigned to **Linux-A-VM**.  If you do not have a SSH client installed, use the following website and scan for the SSH service - https://dnschecker.org/port-scanner.php.  Select **Port Type**:  "**Server Ports**".
    
Why is HTTPS showing up on the scan results?


**Linux-B-VM** is the www server and should have the following access:
- HTTP and HTTPS access to the Internet
- PING access to **Linux-A-VM**
- HTTP service available from the Internet

- 2. From the **Linux-B-VM** CLI:
        - Confirm port 80 access to the Internet:  "**wget www.fortinet.com**"
        - Confirm port 443 access to the Internet and the public IP assigned to **Linux-B-VM**: "**curl https://ipinfo.io/ip**"  (Confirm against what the Azure portal has listed  as the Public IP assigned to the FortiGate or confirm against the IP you used to login to the FortiGate GUI.)
        - Ping the private IP of **Linux-A-VM** and confirm replies.
        - From your local browser, open a tab and enter "**http://x.x.x.x**"  (x.x.x.x is the VIP of **Linux-B-VM**)  Confirm you get an NGINX welcome screen.
        
Congrats if you confirmed access on all the requirements above on the first check.

If time permits try enabling other ports on the Linux VMs and allowing access via the FortiGate.
Also, spend some time looking around the FortiGate NVA GUI and see if you notice differences between what options are available compared to the FortiGate hardware GUI.

Thanks for attending this course.

**END OF COURSE**



