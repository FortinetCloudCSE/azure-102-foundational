---
title: "Task 3:  Confirm Linux VMs access via FortiGate"
weight: 4
---

In Task 3, you will confirm the Linux VMs are using the FortiGate NVA as their default route and that all traffic to/from the Linux VMs is going through the FortiGate.

1. ***Open*** Serial consoles **linux-a-vm** and **linux-b-vm**

1. ***From*** **linux-a-vm** console run

    - `ping www.yahoo.com`
    - `ping 192.168.1.164`

    Neither should respond

    {{< figure src="azure-access-fgt-1.png" alt="azure-access-fgt-1" >}}

1. ***From*** **linux-b-vm** console run

    - `ping www.yahoo.com`
    - `ping 192.168.1.132`

    Neither should respond

    {{< figure src="azure-access-fgt-2.png" alt="azure-access-fgt-2" >}}

1. ***Login*** to the FortiGate

1. ***Open*** a CLI session on the FortiGate

    {{< figure src="azure-access-fgt-3.png" alt="azure-access-fgt-3" >}}

1. Enter the FortiGate CLI command

    - `diagnose sniffer packet port2 'icmp'`

1. Run steps two and three again.

    The ICMP echo request traffic reaches the FortiGate, however the FortiGate does not have any policies to allow or deny the traffic.

    {{< figure src="azure-access-fgt-4.png" alt="azure-access-fgt-4" >}}
