
# Project 5 — Microsoft Sentinel (SIEM)

## What this is about

This project is about setting up Microsoft Sentinel as a cloud-native SIEM/SOAR solution. The goal was to get hands-on with log ingestion, data connectors, and writing detection rules using KQL — the kind of work you'd actually do in a SOC environment.

## Tools and technologies

- Microsoft Sentinel
- Log Analytics Workspace
- Azure Activity connector
- KQL (Kusto Query Language)
- Analytics Rules (Scheduled)

## What I built

### 1. Log Analytics Workspace

First thing was creating the workspace that Sentinel would sit on top of. Nothing fancy here — just making sure it was in the right region and resource group before connecting anything else.

- Name: `law-security-lab`
- Region: East US
- Resource Group: `rg-security-lab`

### 2. Connecting Microsoft Sentinel

Once the workspace was ready, I linked Sentinel to it. This is the step that activates all the SIEM functionality — without the workspace, Sentinel has nowhere to store or query logs.

### 3. Data Connector — Azure Activity

I enabled the Azure Activity connector to start pulling in subscription-level logs. This gives visibility into what's happening across the environment: who's deploying resources, changing configurations, or doing anything that touches the Azure control plane.

- Status: Connected
- Coverage: full subscription activity log ingestion

### 4. Detection Rule — Suspicious Resource Deployment

This was the most interesting part. I created a scheduled analytics rule to flag unusual resource deployments — specifically, deployments made by callers that haven't been seen before in the environment.

The idea behind this rule is that attackers who gain access to an Azure subscription often try to spin up resources quickly (cryptominers, C2 infrastructure, etc.). Detecting first-time deployers is a simple but effective signal.

- Type: Scheduled
- Severity: Low
- MITRE ATT&CK: Impact — T1496 (Resource Hijacking)
- Frequency: runs every day, looks back 14 days

## Screenshots

| File | What it shows |
|------|---------------|
| 01-sentinel-no-workspace.png | Starting state — Sentinel before workspace setup |
| 02-sentinel-created.png | Sentinel successfully created |
| 03-sentinel-overview.png | Main dashboard after setup |
| 04-sentinel-data-connectors.png | Data Connectors page |
| 05-sentinel-connectors-connected.png | Azure Activity connector in Connected state |
| 06-sentinel-azure-activity-installed.png | Azure Activity content hub installed |
| 07-analytics-rule-created.png | Detection rule showing up in the Analytics list |
| 08-analytics-rule-detail.png | Rule configuration and KQL query detail |
| 09-law-workspace.png | Log Analytics Workspace active and linked |

## Skills this project covers

- Deploying and configuring a cloud SIEM (Microsoft Sentinel)
- Connecting data sources through native connectors
- Writing detection logic with KQL
- Mapping detections to MITRE ATT&CK techniques
- Monitoring Azure resource activity at scale

## Why this matters professionally

Microsoft Sentinel is one of the most widely used SIEMs in enterprise environments right now, especially in Azure-heavy organizations. Understanding how to configure it, connect data sources, and write detection rules is core to SOC Analyst and Security Engineer roles. This lab covers the fundamentals of that workflow end to end.