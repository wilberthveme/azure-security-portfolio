# Azure Cloud Security Portfolio

Hands-on cloud security projects built in Microsoft Azure, documented like real work — not just tutorial screenshots.

![Azure](https://img.shields.io/badge/Azure-0078D4?style=flat&logo=microsoftazure&logoColor=white)
![Entra ID](https://img.shields.io/badge/Entra%20ID-0078D4?style=flat&logo=microsoftazure&logoColor=white)
![Sentinel](https://img.shields.io/badge/Microsoft%20Sentinel-0078D4?style=flat)
![KQL](https://img.shields.io/badge/KQL-orange?style=flat)
![Zero Trust](https://img.shields.io/badge/Zero%20Trust-2E7D32?style=flat)

## About this portfolio

I hold the **Microsoft Certified: Azure Fundamentals (AZ-900)** and **Security, Compliance, and Identity Fundamentals (SC-900)** certifications, and I'm currently working through the **SC-200 (Security Operations Analyst)** learning path. This repository documents 10 hands-on projects I built in Azure covering identity, network security, threat detection, secrets management, governance, and data protection — brought together under a single Zero Trust architecture.

Every project follows the same format: **what I built, why it matters, and screenshots proving it actually works.** No copy-pasted theory — each README explains the reasoning behind the configuration choices, not just the steps.

This portfolio reflects my hands-on experience building Azure security solutions while continuously expanding my knowledge in cloud security.

## Skills Demonstrated

- Identity and Access Management
- Microsoft Entra ID
- Azure RBAC
- Multi-Factor Authentication
- Microsoft Sentinel
- Microsoft Defender for Cloud
- Azure Key Vault
- Microsoft Purview
- Zero Trust
- KQL
- Azure Networking

## 🔎 Start here

If you only look at two projects, look at these:

| Project | Why it stands out |
|---|---|
| **[Project 10 — Zero Trust Architecture](./Project-10-Zero-Trust)** | Ties all 9 other projects into a single Zero Trust model — shows I understand how the pieces fit together, not just individual tools. |
| **[Project 6 — Brute Force Detection with KQL](./Project-6-Brute-Force-Detection)** | A real KQL detection rule mapped to MITRE ATT&CK (T1110), turned into an automated Sentinel Analytics Rule. |

## 📂 All projects

| # | Project | Focus area | Key skills |
|---|---|---|---|
| 1 | [Identity and Access Management](./Project-1-IAM) | Identity | Microsoft Entra ID, MFA, RBAC, Security Groups |
| 2 | [Secure Network Architecture](./Project-2-Network) | Network | VNet, Subnets, NSG rules, least-privilege network access |
| 3 | [Secure VM Access with Bastion](./Project-3-Bastion) | Secure Access | Azure Bastion, zero public IP exposure |
| 4 | [Microsoft Defender for Cloud](./Project-4-Defender) | Threat Protection | CSPM, Secure Score, security recommendations |
| 5 | [Microsoft Sentinel Setup](./Project-5-Sentinel) | SIEM | Log Analytics Workspace, data connectors |
| 6 | [Brute Force Detection with KQL](./Project-6-Brute-Force-Detection) | Detection Engineering | KQL, Analytics Rules, MITRE ATT&CK mapping |
| 7 | [Azure Key Vault](./Project-7-Key-Vault) | Secrets Management | RBAC permission model, audit logging |
| 8 | [Security Audit](./Project-8-Security-Audit) | Governance | Azure Policy, Secure Score, compliance reporting |
| 9 | [Microsoft Purview](./Project-9-Purview) | Data Protection | Data Map, classification rules, sensitive data discovery |
| 10 | [Zero Trust Architecture](./Project-10-Zero-Trust) | Synthesis | Maps all projects to the Zero Trust model |

## 🧠 Why Zero Trust ties it together

```
Identity (P1) → Network (P2) → Secure Access (P3) → Threat Detection (P4-P6) → Secrets & Data (P7, P9) → Governance (P8)
                                        all mapped to Zero Trust in P10
```

Each project isn't an isolated exercise — it's one control in a Zero Trust model. See [Project 10](./Project-10-Zero-Trust) for the full breakdown.

## Repository Structure

Each project README follows the same structure, so you know what to expect before opening it:

- **Overview** — the problem the project solves and the context behind it
- **What I used** — the Azure services and tools involved
- **What I built** — step-by-step breakdown of the implementation
- **Why this matters** — the security concept behind the configuration, connected to real-world risk
- **Screenshots** — visual proof of each step, in order

## Roadmap

Upcoming projects include:

- End-to-end incident investigation
- Defender for Endpoint
- Microsoft Sentinel automation
- Threat hunting with KQL

## 📫 Contact

- LinkedIn: [linkedin.com/in/wilbert-vega-mendoza](https://www.linkedin.com/in/wilbert-vega-mendoza-82380514a/)
- GitHub: [github.com/wilberthveme](https://github.com/wilberthveme)
- Email: [wilberthveme@gmail.com](mailto:wilberthveme@gmail.com)

