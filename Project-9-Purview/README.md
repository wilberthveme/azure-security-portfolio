
# Project 9 — Microsoft Purview (Data Classification and Protection)

## Overview

Knowing what data you have and where it lives is the foundation of data security. This project covers Microsoft Purview — Azure's data governance platform — which scans data sources, automatically classifies sensitive information, and gives security teams the visibility they need to protect it.

## What I used

- Microsoft Purview
- Azure Blob Storage (as data source)
- Purview Data Map
- Classifications and Classification Rules

## What I built

### Purview Account

Created a Microsoft Purview account connected to the lab environment. Purview acts as a central catalog — it discovers data across your Azure resources, classifies it based on content, and maps where sensitive data lives.

- **Name:** `purview-security-lab`
- **Resource Group:** `rg-security-lab`
- **Region:** West US 3

### Data Map and Collections

The Data Map is where Purview organizes everything it discovers. Collections are containers that group data sources together — similar to how resource groups work in Azure. The root collection `purview-security-lab` is the starting point for registering data sources.

### Classifications

Purview comes with hundreds of built-in classification rules that automatically detect sensitive data patterns — credit card numbers, national ID numbers, passport numbers, email addresses, and more. These rules run during scans and tag assets with the appropriate classification.

In a real environment, this means you could scan a storage account with thousands of files and Purview would automatically identify which ones contain PII, financial data, or health records — without anyone having to open each file manually.

### Data Sources

Explored the full catalog of supported data sources — Azure Blob Storage, Azure SQL, Cosmos DB, Data Lake, and many others. Registered Azure Blob Storage as a data source to demonstrate how Purview connects to storage and prepares it for scanning.

In production, once a data source is registered you schedule a scan, Purview crawls the data, applies classification rules, and surfaces the results in the catalog.

## Why this matters

Data governance is a core requirement in regulated industries — finance, healthcare, government. Knowing where your sensitive data is isn't optional, it's a compliance requirement (GDPR, HIPAA, PCI-DSS). Purview automates that discovery process at scale.

From a security perspective, you can't protect what you don't know you have. Purview gives security teams a map of sensitive data across the entire environment, which feeds directly into decisions about access controls, encryption, and monitoring. This connects to the Zero Trust principle of protecting data regardless of where it lives.

## Screenshots

| File | What it shows |
|------|---------------|
| [01-purview-created.png](./Screenshots/01-purview-created.png) | Microsoft Purview account created |
| [02-purview-collections.png](./Screenshots/02-purview-collections.png) | Purview portal - Collections overview |
| [03-purview-classifications.png](./Screenshots/03-purview-classifications.png) | Built-in classification types |
| [04-purview-classification-rules.png](./Screenshots/04-purview-classification-rules.png) | Classification rules for sensitive data detection |
| [05-purview-data-sources.png](./Screenshots/05-purview-data-sources.png) | Data Map showing registered sources |
| [06-purview-data-sources-available.png](./Screenshots/06-purview-data-sources-available.png) | Full catalog of supported Azure data sources |
| [07-purview-register-blob.png](./Screenshots/07-purview-register-blob.png) | Azure Blob Storage registration form |