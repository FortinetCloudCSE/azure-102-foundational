---
title: "Chapter 1: Architecture"
weight: 5
---

## Azure Reference Architecture Diagrams

Azure networking offers multiple ways to organize your Azure architecture to take advantage of FortiGate traffic inspection.  Most importantly, traffic must follow a symmetrical routing path (for forward and reverse flows). As long as flows are symmetrical, the architecture will work and traffic will flow through a FortiGate NGFW for inspection.

During this course the following two architectures will be deployed:

### Single VNET without a FortiGate NVA - Unsecured VNET

  {{< figure src="azure-unsecured-vnet.png" alt="azure-unsecured-vnet" >}}

### Single VNET with a FortiGate NVA - Secured VNET

  {{< figure src="azure-secured-vnet.png" alt="azure-secured-vnet" >}}
