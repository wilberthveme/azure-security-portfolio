
# Project 4 — Microsoft Defender for Cloud

## Overview

Before you can respond to threats, you need visibility. This project is about setting up Microsoft Defender for Cloud to get a clear picture of the security posture across the Azure environment — what's exposed, what's misconfigured, and what needs attention.

## What I used

- Microsoft Defender for Cloud
- Azure Subscription (Free Trial)
- Foundational CSPM (free tier)

## What I did

### Explored the main dashboard

The Defender for Cloud overview gives you a consolidated view of everything: subscriptions being monitored, current security posture, attack path analysis, and active alerts. Getting familiar with this dashboard is important — in a SOC environment, this is one of the first places you'd look when assessing an Azure tenant.

### Reviewed Defender plans

One of the first things I checked was making sure no paid plans were accidentally enabled. Defender plans can rack up costs fast, and on a free trial you want to be deliberate about what's on.

- **Foundational CSPM:** Free ✅ — continuous security assessment at no cost
- All paid workload protection plans (Servers, App Service, Databases, Storage, Defender CSPM): Off

The free tier still gives you Secure Score and security recommendations, which is enough to demonstrate the core concepts.

### Configured email notifications

Set up alerts so that any high severity security event triggers an email notification. Small step, but in a real environment you'd never want these going unmonitored — silent alerts are as good as no alerts.

- Severity threshold: High and above
- Recipient: Owner role

## Why this matters

Defender for Cloud is a daily tool in SOC and cloud security roles. The Secure Score gives you a prioritized list of what to fix, recommendations guide the actual remediation work, and the alerts feed directly into Microsoft Sentinel — which is exactly what Project 5 builds on. Understanding how these two services connect is core to the SC-200 exam and to the SOC Analyst role in general.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-defender-overview.png](./Screenshots/01-defender-overview.png) | Defender for Cloud main dashboard |
| [02-defender-plans-off.png](./Screenshots/02-defender-plans-off.png) | All paid Defender plans disabled |
| [03-defender-email-notifications.png](./Screenshots/03-defender-email-notifications.png) | Email notifications configured for high severity alerts |