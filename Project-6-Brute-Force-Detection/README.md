
# Project 6 — Brute Force Detection with KQL

## Overview

Having a SIEM is only useful if it's actually detecting something. This project is about writing a KQL query that identifies brute force patterns in Azure Activity logs — multiple failed operations from the same source — and turning it into an automated detection rule in Microsoft Sentinel.

## What I used

- Microsoft Sentinel
- Log Analytics Workspace
- Azure Activity connector
- KQL (Kusto Query Language)
- Analytics Rules (Scheduled)

## What I built

### Log Analytics Workspace

Set up the workspace that Sentinel uses to store and query logs.

- Name: `law-security-lab`
- Region: East US
- Resource Group: `rg-security-lab`

### Microsoft Sentinel

Connected Sentinel to the workspace and linked it to the Microsoft Defender portal for unified visibility.

### Azure Activity Connector

Connected the Azure Activity data source using the diagnostics settings pipeline. This streams subscription-level activity logs — who did what, when, and from where — directly into the workspace.

### Brute Force Detection Query

The core of this project. The query looks for repeated failures from the same IP address and caller — the classic signature of a brute force or credential stuffing attack.

```kql
AzureActivity
| where ActivityStatusValue == "Failure"
| where TimeGenerated > ago(24h)
| summarize FailureCount = count() by CallerIpAddress, Caller, OperationNameValue
| where FailureCount >= 5
| sort by FailureCount desc
```

What each part does:
- Filter to failed operations only
- Look back 24 hours
- Group by IP, caller identity, and operation type
- Surface only sources with 5 or more failures
- Sort by highest failure count first

The threshold of 5 is a starting point — in a real environment you'd tune this based on baseline behavior to reduce false positives.

### Analytics Rule — Brute Force Detection

Turned the query into a scheduled rule so Sentinel runs it automatically and generates an alert when the threshold is hit.

- **Name:** Brute Force Detection - Failed Operations
- **Severity:** Medium
- **Query frequency:** Every 1 hour
- **Lookback period:** Last 24 hours
- **Alert trigger:** Results greater than 0
- **MITRE ATT&CK:** Credential Access — T1110 (Brute Force)

## Why this matters

Brute force attacks against Azure management APIs are common — attackers who get a foothold try to escalate by hammering authentication endpoints. This rule gives a SOC team an automated signal when that pattern appears, instead of relying on someone manually reviewing logs. It's a foundational detection that most SOC environments have in some form.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-law-workspace-created.png](./Screenshots/01-law-workspace-created.png) | Log Analytics Workspace created |
| [02-sentinel-created.png](./Screenshots/02-sentinel-created.png) | Microsoft Sentinel connected to workspace |
| [03-workspace-connected.png](./Screenshots/03-workspace-connected.png) | Workspace connected to Microsoft Defender portal |
| [04-azure-activity-connected.png](./Screenshots/04-azure-activity-connected.png) | Azure Activity connector in Connected state |
| [05-analytics-rule-logic.png](./Screenshots/05-analytics-rule-logic.png) | KQL query and rule configuration |
| [06-analytics-rule-created.png](./Screenshots/06-analytics-rule-created.png) | Detection rule active in Analytics list |