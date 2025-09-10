---
title: "Chapter 1: Architecture Diagrams"
weight: 5
---


Upon completion of this workshop, you will gain understanding of, create, and deploy the following:

- Azure Services
- Azure Virtual Network (VNET)
- FortiGate-VM support for Azure
- Create an Azure unsecured VNET
- Deploy a FortiGate-VM to create an Azure secured VNET
- Configure FortiGate firewall policies to control access to/from the Internet

## Azure Reference Architecture Diagrams

- Azure networking offers multiple ways to organize your Azure architecture to take advantage of FortiGate traffic inspection.  Most importantly, traffic must follow a symmetrical routing path (for forward and reverse flows). As long as flows are symmetrical, the architecture will work and traffic will flow through a FortiGate NGFW for inspection.

- You will deploy and configure the following two architectures:
  - **Single VNET without a FortiGate NVA - Unsecured VNET**

  {{< figure src="Azure-Unsecured-VNET1.PNG" alt="Azure-Unsecured-VNET1" >}}

  - **Single VNET with a FortiGate NVA - Secured VNET**

  {{< figure src="Azure-Secured-VNET.PNG" alt="Azure-Secured-VNET" >}}

**Continue to Chapter 2: Azure Fundamentals**