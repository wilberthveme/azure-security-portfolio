
# Project 1 — Identity and Access Management (IAM)

## Overview

One of the first things any security setup needs is a solid identity foundation. This project covers building that in Azure — users, groups, MFA, and role assignments — using Microsoft Entra ID to simulate how a real company would structure access.

Nothing groundbreaking, but getting this right is what everything else builds on.

## What I used

- Microsoft Azure
- Microsoft Entra ID

## What I did

### Users

Created three users representing different roles inside a company:

- `admin.company` — full administrator
- `analyst.company` — security analyst with limited access
- `guest.company` — external user with minimal permissions

The idea was to have a realistic mix of access levels rather than just one test account.

### Groups

Organized users into two security groups:

- `Administrators` — contains admin.company
- `Analysts` — contains analyst.company

Guest.company stays outside any group intentionally — not everyone in an org needs to belong to a group.

### Dynamic Groups (free tier limitation)

Dynamic groups need an Entra ID P1 license, which isn't available on the free tier. In a real environment, you'd use these to automatically assign users to groups based on attributes like job title or department — no manual management needed. Something worth noting for production setups.

### MFA

Enabled Multi-Factor Authentication for admin.company and analyst.company. Guest.company was left without it on purpose — to show that not all roles carry the same security requirements, and that MFA decisions should follow the sensitivity of the access, not be applied blindly to everyone.

### RBAC and Least Privilege

Assigned roles based on what each user actually needs:

- `admin.company` — Owner (full control)
- `analyst.company` — Reader (read-only)
- `guest.company` — no role assigned

The principle here is simple: nobody gets more access than their job requires. Overprivileged accounts are one of the most common ways breaches escalate.

### Conditional Access (free tier limitation)

Like dynamic groups, Conditional Access policies require P1. In practice, you'd use these to enforce MFA selectively — for example, only when someone logs in from an untrusted location or a flagged IP. It's a much smarter approach than blanket MFA for everything.

## Screenshots

All screenshots are in the [screenshots](./screenshots) folder.