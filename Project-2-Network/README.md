
# Project 2 — Secure Network Architecture in Azure

## Overview

Before deploying anything in the cloud, you need to think about network boundaries. This project is about building a segmented network in Azure — separating public-facing resources from internal ones, and locking down traffic with NSG rules so nothing gets in unless it's supposed to.

## What I used

- Microsoft Azure
- Azure Virtual Networks (VNet)
- Network Security Groups (NSG)

## What I built

### Virtual Network

Set up a VNet as the foundation for all lab resources:

- **Name:** `vnet-security-lab`
- **Resource Group:** `rg-security-lab`
- **Region:** East US
- **Address space:** `10.0.0.0/16`

A /16 gives plenty of room to grow — important when you're planning a lab that will keep expanding.

### Subnets

Split the network into two subnets with different exposure levels:

**Public subnet** (`subnet-public` — `10.0.0.0/24`)
Meant for resources that need internet-facing access. Not wide open — traffic is controlled through the NSG.

**Private subnet** (`subnet-private` — `10.0.1.0/24`)
No default outbound access. Resources here can't reach the internet unless explicitly allowed, which is exactly the point.

### Network Security Group

Created `nsg-security-lab` and attached it to the public subnet. The NSG is what actually enforces the rules — without it, the subnet is just a label.

### Inbound rules

This is where least privilege shows up at the network level. Instead of leaving RDP open to the world (a very common misconfiguration), I restricted it to a single IP:

| Priority | Rule | Port | Source | Action |
|----------|------|------|--------|--------|
| 100 | Allow-RDP-MyIP | 3389 | My IP only | Allow |
| 200 | Deny-RDP-All | 3389 | Any | Deny |

Priority 100 runs first — my IP gets through. Everything else hits the deny rule at 200. Simple, but this alone blocks a massive amount of automated RDP scanning that happens constantly on public cloud IPs.

## Screenshots

| File | What it shows |
|------|---------------|
| [00-virtual-networks-empty.png](./Screenshots/00-virtual-networks-empty.png) | Virtual Networks before setup |
| [01-subnet-private-config.png](./Screenshots/01-subnet-private-config.png) | Private subnet configuration |
| [02-subnets-created.png](./Screenshots/02-subnets-created.png) | Both subnets created |
| [03-vnet-review.png](./Screenshots/03-vnet-review.png) | VNet review before deployment |
| [04-vnet-created.png](./Screenshots/04-vnet-created.png) | VNet successfully created |
| [06-nsg-created.png](./Screenshots/06-nsg-created.png) | NSG created |
| [07-nsg-default-rules.png](./Screenshots/07-nsg-default-rules.png) | Default inbound rules before customization |
| [08-nsg-rdp-rule.png](./Screenshots/08-nsg-rdp-rule.png) | RDP rule configuration |
| [09-nsg-rdp-rule-created.png](./Screenshots/09-nsg-rdp-rule-created.png) | RDP rule created |
| [10-nsg-rules-created.png](./Screenshots/10-nsg-rules-created.png) | All NSG rules in place |
| [11-nsg-associated-subnet.png](./Screenshots/11-nsg-associated-subnet.png) | NSG associated to public subnet |