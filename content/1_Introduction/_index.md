---
title: "Chapter 1: Architecture Diagrams"
weight: 5
---


Upon completion of this workshop, you will gain understanding, create, and deploy the following:
  * Azure Services
  * Azure Virtual Network (VNET)
  * FortiGate-VM support for Azure
  * Create an Azure unsecured VNET
  * Deploy a FortiGate-VM to create an Azure secured VNET
  * Configure FortiGate firewall policies to control access to/from the Internet

<!--
## Workshop Components

Fortinet & Azure compute and components used during this workshop:

  * Azure Fsv2 series instances running a FortiGate NVA
  * Azure DsV4 series instances running Ubuntu Linux OS as the testing workloads
  * Azure Networking Components:
    * Virtual Network (vNET)
    * Subnets
    * NAT Gateway
    * User-defined Route Table (UDR)
-->

## Azure Reference Architecture Diagrams

  * Azure networking offers multiple ways to organize your Azure architecture to take advantage of FortiGate traffic inspection.  Most importantly, traffic must follow a symmetrical routing path (for forward and reverse flows). As long as flows are symmetrical, the architecture will work and traffic will flow through a FortiGate NGFW for inspection.

  * You will deploy and configure the following two architectures:
    - **Single VNET without a FortiGate NVA - Unsecured VNET**
![](Images/Azure-Unsecured-VNET1.PNG)


    - **Single VNET with a FortiGate NVA - Secured VNET**
![](Images/Azure-Secured-VNET.PNG)

**Continue to Chapter 2: Azure Fundamentals**