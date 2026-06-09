
# Project 2: Secure Network in Azure
## Azure Cloud Security Portfolio

## Objective
Implement a secure network architecture in Azure using Virtual Networks, public and private subnets, and Network Security Groups (NSG) to control and restrict traffic following security best practices.

## Skills Learned
- Network segmentation
- Virtual Network (VNet) configuration
- Subnet design (public and private)
- Network Security Groups (NSG)
- Inbound and outbound traffic control
- Least privilege applied to network access

## Tools Used
- Microsoft Azure
- Azure Virtual Networks
- Network Security Groups (NSG)

## Steps

### 1. Created Virtual Network
Created a Virtual Network to host all lab resources:
- **Name:** vnet-security-lab
- **Resource Group:** rg-security-lab
- **Region:** East US
- **Address space:** 10.0.0.0/16 (65,536 addresses)

### 2. Created Subnets
Segmented the network into two subnets following security best practices:

**Public Subnet:**
- **Name:** subnet-public
- **Address range:** 10.0.0.0/24 (256 addresses)
- Accessible from the internet with controlled rules

**Private Subnet:**
- **Name:** subnet-private
- **Address range:** 10.0.1.0/24 (256 addresses)
- No default outbound access (private subnet enabled)

### 3. Created Network Security Group
Created an NSG to control traffic to the public subnet:
- **Name:** nsg-security-lab
- **Resource Group:** rg-security-lab

### 4. Configured Inbound Security Rules
Added custom rules following the Least Privilege principle:

| Priority | Name | Port | Source | Action |
|---|---|---|---|---|
| 100 | Allow-RDP-MyIP | 3389 | My IP only | Allow |
| 200 | Deny-RDP-All | 3389 | Any | Deny |

### 5. Associated NSG to Public Subnet
Associated nsg-security-lab to subnet-public to enforce the security rules on all traffic entering and leaving the public subnet.

## Screenshots
All screenshots are available in the [Screenshots](./Screenshots) folder.