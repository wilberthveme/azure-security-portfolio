
# Project 7 — Azure Key Vault

## Overview

Hardcoded credentials are one of the most common causes of security breaches in cloud environments. This project is about solving that problem using Azure Key Vault — a managed service for storing secrets, API keys, and certificates so they never have to live in application code.

## What I used

- Azure Key Vault
- Azure RBAC (Role-Based Access Control)
- Diagnostic settings (Audit logging)

## What I built

### Key Vault

Created the vault that will store all sensitive credentials for the lab environment.

- **Name:** `kv-security-lab`
- **Resource Group:** `rg-security-lab`
- **Region:** East US
- **Permission model:** Azure RBAC

Chose RBAC over the legacy Access Policies model — RBAC is the modern approach and gives more granular control over who can do what with each secret.

### Role Assignment

Assigned the **Key Vault Secrets Officer** role to my account at the vault scope. This role allows creating, reading, and managing secrets without granting full control over the vault configuration itself.

The difference matters — an Owner can delete the vault or change who has access. A Secrets Officer can only work with the secrets inside it. That's least privilege in practice.

### Secrets

Created two secrets simulating a real application environment:

**`db-password`** — database connection password
In a real app, this would be the production database password. Instead of writing it in the connection string inside the code, the app retrieves it from Key Vault at runtime. If someone steals the codebase, they get nothing useful.

**`api-key`** — third-party API key
Simulates a key for an external service like Stripe or a mapping API. Same principle — the key lives in the vault, not in the source code or environment files.

### Audit Logging

Configured diagnostic settings to capture **AuditEvent** logs for the vault. Every time a secret is accessed, created, or deleted, that action gets logged — including who did it and when.

In a SOC environment, this audit trail is critical. If credentials are ever compromised, you can look at the Key Vault logs to see exactly when they were accessed and by whom.

## Why this matters

Credential exposure through source code is consistently one of the top attack vectors in cloud environments. Developers accidentally push API keys to public GitHub repos, or leave passwords in config files that end up in version control. Key Vault eliminates that entire category of risk by giving applications a secure, auditable way to retrieve secrets without ever storing them in the code.

This connects directly to Zero Trust principles — never embed trust in static credentials that can be stolen. Instead, enforce identity-based access to secrets with full audit logging.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-keyvault-access-config.png](./Screenshots/01-keyvault-access-config.png) | Access configuration with RBAC permission model |
| [02-keyvault-created.png](./Screenshots/02-keyvault-created.png) | Key Vault successfully created |
| [03-keyvault-rbac-assigned.png](./Screenshots/03-keyvault-rbac-assigned.png) | Key Vault Secrets Officer role assigned |
| [04-keyvault-secret-created.png](./Screenshots/04-keyvault-secret-created.png) | First secret (db-password) created |
| [05-keyvault-secret-detail.png](./Screenshots/05-keyvault-secret-detail.png) | Secret detail view — value is not visible |
| [06-keyvault-two-secrets.png](./Screenshots/06-keyvault-two-secrets.png) | Both secrets created (db-password and api-key) |
| [07-keyvault-diagnostic-setting.png](./Screenshots/07-keyvault-diagnostic-setting.png) | Audit logging configured for the vault |