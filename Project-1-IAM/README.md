# Project 1: Identity and Access Management (IAM)
## Azure Cloud Security Portfolio

## Objective
Implement a secure Identity and Access Management environment in Microsoft Azure using Microsoft Entra ID, simulating a real company with multiple users and different access levels.

## Skills Learned
- Identity and Access Management (IAM)
- Role-Based Access Control (RBAC)
- Multi-Factor Authentication (MFA)
- Zero Trust principles
- Least Privilege principle

## Tools Used
- Microsoft Azure
- Microsoft Entra ID

## Steps

### 1. Created Users
Created 3 users simulating company employees:
- `admin.company` — Administrator
- `analyst.company` — Security Analyst
- `guest.company` — Guest user

### 2. Created Groups
Created 2 security groups:
- `Administrators` — contains admin.company
- `Analysts` — contains analyst.company

### 3. Dynamic Groups (License Limitation)
Dynamic groups require Microsoft Entra ID P1 license — not available on Free tier. In a production environment, dynamic groups would automatically assign users based on attributes such as job title or department.

### 4. Configured MFA
Enabled Multi-Factor Authentication for:
- admin.company
- analyst.company

Guest.company was left without MFA to demonstrate different security levels per role.

### 5. Implemented RBAC and Least Privilege
Assigned roles following the Least Privilege principle:
- `admin.company` — Owner (full control)
- `analyst.company` — Reader (read-only)
- `guest.company` — No role assigned (minimum access)

### 6. Conditional Access (License Limitation)
Conditional Access policies require Microsoft Entra ID P1 license. In a production environment, Conditional Access would enforce MFA only when users sign in from outside trusted locations or from risky IP addresses.

## Screenshots
All screenshots are available in the [screenshots](./screenshots) folder.