
# Project 8 — Security Audit

## Overview

Deploying resources in Azure is easy. Keeping them secure and compliant over time is a different problem. This project covers the governance and auditing side of cloud security — using Azure Policy to enforce rules across the environment, reviewing compliance reports to see what's drifting, and using Defender for Cloud's Secure Score to prioritize what to fix.

## What I used

- Microsoft Defender for Cloud
- Azure Policy
- Policy Compliance Reports

## What I built

### Secure Score Review

Starting point for any security audit is understanding the current posture. Defender for Cloud's Secure Score gives a single number — in this environment, **25%** — along with a prioritized list of recommendations.

The recommendations surfaced for this environment were mostly around the `vm-target-lab` VM:
- No SSH key authentication enforced
- No disk encryption enabled
- No vulnerability assessment solution installed
- Missing system update checks

This is exactly the kind of finding a security team would act on after an audit. The score gives you the "what", and the recommendations give you the "how to fix it".

### Azure Policy — Require Tags on Resources

Created a policy assignment to enforce that all resources in the subscription have an `Environment: Lab` tag. Tags are how organizations track ownership, cost allocation, and environment classification at scale.

- **Policy:** Require a tag and its value on resources
- **Tag Name:** `Environment`
- **Tag Value:** `Lab`
- **Scope:** Azure subscription 1

In a production environment, you'd require tags like `Owner`, `CostCenter`, or `Project` so every resource can be traced back to a team and a budget.

### Compliance Report

After assigning the policy, Azure evaluated all existing resources against it. The result: **0% compliance** — 8 out of 8 resources were missing the required tag.

This is the expected outcome when you apply a new governance policy to an existing environment — existing resources don't automatically comply, they need to be remediated. The report gives you the full list of non-compliant resources so you know exactly what needs to be fixed.

The Azure Activity log policies, on the other hand, showed **100% compliant** — those were already configured correctly from Project 6.

## Why this matters

Governance and compliance are core responsibilities in cloud security roles. A misconfigured resource that nobody owns is a risk — you can't protect what you can't track. Azure Policy is how security teams enforce guardrails at scale, and the compliance report is how they prove to auditors that those guardrails are working.

The Secure Score adds a continuous improvement layer — it's not just about passing an audit once, it's about having a measurable baseline and tracking progress over time. Both of these are daily tools for SOC Analysts and Cloud Security Engineers.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-secure-score.png](./Screenshots/01-secure-score.png) | Secure Score at 25% with 2 unhealthy resources |
| [02-secure-score-recommendations.png](./Screenshots/02-secure-score-recommendations.png) | Full list of security recommendations |
| [03-azure-policy-definitions.png](./Screenshots/03-azure-policy-definitions.png) | Azure Policy definitions filtered by tag |
| [04-azure-policy-assign.png](./Screenshots/04-azure-policy-assign.png) | Policy assignment configuration |
| [05-azure-policy-assigned.png](./Screenshots/05-azure-policy-assigned.png) | Policy active in assignments list |
| [06-compliance-report.png](./Screenshots/06-compliance-report.png) | Compliance report showing non-compliant resources |
