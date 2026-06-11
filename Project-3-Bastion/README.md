
# Project 3 — Secure VM Access with Azure Bastion

## Overview

One of the easiest ways to get compromised in the cloud is leaving SSH or RDP ports exposed to the internet. This project solves that problem using Azure Bastion — a managed service that lets you connect to VMs through the browser without any public IP or open ports on the machine itself.

## What I used

- Microsoft Azure
- Azure Bastion (SKU Standard)
- Azure Virtual Machines (Ubuntu 24.04)
- Azure Virtual Network

## What I built

### AzureBastionSubnet

Bastion requires its own dedicated subnet — Azure is strict about the name, it has to be exactly `AzureBastionSubnet` or the deployment fails. Added it inside the existing `vnet-security-lab`:

- **Address range:** `10.0.2.0/26` (64 addresses, which is the minimum Bastion needs)

### Azure Bastion resource

Deployed the Bastion service with a public IP and connected it to the VNet. The public IP here is for Bastion itself, not the VM — Bastion sits in the middle and brokers the connection, so the VM stays completely off the internet.

### Linux VM with no public IP

Deployed the VM with no public IP assigned. No public IP means no attack surface — there's nothing for a port scanner to find, no SSH brute force attempts, nothing. The only way in is through Bastion.

### SSH session via browser

Connected to the VM through the Azure portal using Bastion and verified the hostname from inside the session. No SSH client needed, no key file management — just a browser session running over HTTPS. All access is logged and tied to your Azure identity.

### Cleanup

Deleted the Bastion resource after the lab. Bastion is one of the pricier services in Azure — leaving it running burns through free credits fast. In a real environment you'd keep it up, but for a lab, spinning it down when you're done is just good practice.

## Why this matters

Exposed SSH and RDP ports are consistently among the top sources of cloud compromises. Bastion eliminates that entire category of risk. In any real production environment, direct VM access should work exactly like this — never through a public IP.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-bastion-subnet-created.png](./Screenshots/01-bastion-subnet-created.png) | AzureBastionSubnet created inside the VNet |
| [02-bastion-resource-created.png](./Screenshots/02-bastion-resource-created.png) | Bastion resource successfully deployed |
| [03-bastion-public-ip.png](./Screenshots/03-bastion-public-ip.png) | Public IP assigned to Bastion |
| [04-vm-created-no-public-ip.png](./Screenshots/04-vm-created-no-public-ip.png) | VM created with no public IP |
| [05-vm-no-public-ip.png](./Screenshots/05-vm-no-public-ip.png) | Confirmation that the VM has no public IP |
| [06-bastion-session-active.png](./Screenshots/06-bastion-session-active.png) | Active browser session into the VM via Bastion |
| [07-bastion-session-hostname.png](./Screenshots/07-bastion-session-hostname.png) | Hostname verified from inside the VM |
| [08-bastion-deleted.png](./Screenshots/08-bastion-deleted.png) | Bastion deleted after lab to save credits |