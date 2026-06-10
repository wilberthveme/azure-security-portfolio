
# Project 3: Azure Bastion + Secure VM Access
## Azure Cloud Security Portfolio

## Objective
Implement secure access to a Linux VM without exposing SSH ports to the internet,
using Azure Bastion as a PaaS service managed by Microsoft.

## Skills Learned
- Secure remote access without public IP
- Azure Bastion deployment and configuration
- Network segmentation with private subnets
- Elimination of attack surface (no exposed RDP/SSH ports)
- SSH session via browser using Bastion

## Tools Used
- Microsoft Azure
- Azure Bastion (SKU Standard)
- Azure Virtual Machines (Ubuntu 24.04)
- Azure Virtual Network
- Azure Monitor

## Steps

### 1. Created AzureBastionSubnet
Added a dedicated subnet for Bastion inside vnet-security-lab:
- **Name:** AzureBastionSubnet (exact name required by Azure)
- **Address range:** 10.0.2.0/26 (64 addresses)

### 2. Deployed Azure Bastion
Created Bastion service connected to the VNet:
- **Name:** vnet-security-lab-bastion
- **SKU:** Standard
- **Public IP:** vnet-security-lab-IPv4 (20.81.55.107)

### 3. Created Linux VM without Public IP
Deployed Ubuntu VM with no public IP address: