---
title: "Task 3:  Confirm Linux VMs access via FortiGate"
weight: 4
---

In Task Three, you will confirm the Linux VMs are using the FortiGate NVA as their default route and that all traffic to/from the Linux VMs is going through the FortiGate.

1. Navigate into your **Resource Group** and open, in separate tabs, the **FortiGate** GUI, the **Linux-A-VM** console, and the **Linux-B-VM** console.  

1. From the **Linux-A-VM** console, run the following:

    - `ping www.yahoo.com`
    - `ping 192.168.1.164`

Did you get a response from either?  Why not?

1. From the **Linux-B-VM** console, run the following:

    - `ping www.yahoo.com`
    - `ping 192.168.1.132`

Did you get a response from either?  Why not?

1. From the Fortinet GUI, open a console window, and enter the following command:

    - `diagnose sniffer packet port2 'icmp'`

1. Run steps two and three again.

    Do you see the traffic being reported in the FortiGate console?
    Is the traffic from both Linux VMs being routed to the FortiGate via port2?

1. The diagram below is a visual representation of your VNET with the Linux VMs traffic flow via the FortiGate NVA.  This is now the active flow of traffic based on the UDRs in the Route Table.

    ![4-3-Azure-access-fgt-1](../Images/4-3-Azure-access-fgt-1.PNG)

**Continue to Chapter 5 - Task 4: Configure FortiGate Polices**
