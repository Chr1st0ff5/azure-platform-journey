# AZ-104 — Identity, Governance & Cost (Savill Hour 1)

---

# Microsoft Entra ID (Identity Platform)

## What is Entra ID
Microsoft Entra ID is the cloud identity provider for:

- Azure
- Microsoft 365
- Third-party applications

It manages authentication and access to cloud resources.

Key principle:
Identity exists at tenant level, not subscription.

Tenant = global identity boundary.

---

## Entra ID vs Active Directory (AD DS)

Entra ID is cloud-native, not a direct AD DS replacement.

AD DS:
- Hierarchical OU structure
- LDAP / Kerberos
- On-prem network

Entra ID:
- Flat directory
- Internet protocols
- Cloud APIs

Protocols:
- OAuth2
- OpenID Connect
- SAML
- WS-Fed

All over HTTPS (443).

API:
Microsoft Graph = standard interaction layer.

---

## Tenant Architecture

Tenant = dedicated Entra ID instance for an organization.

Important:
Tenant is NOT inside a subscription.  
Subscriptions trust a tenant for identity.

Hierarchy:

Tenant  
→ Subscriptions  
→ Resource Groups  
→ Resources  

---

## Hybrid Identity

Source of truth:
On-prem AD → Entra ID

Sync technologies:

Entra Connect Sync  
- Sync engine on-prem  

Entra Connect Cloud Sync  
- Cloud engine + local agents  

Purpose:
Extend identities to cloud.

---

## Users

Types:

Cloud-only  
Hybrid (synced)  
Guest (B2B external)  

Guest users keep external identity.

---

## Groups

Types:

Security → permissions  
Microsoft 365 → collaboration  

Membership:

Assigned  
Dynamic (attribute-based rules)

---

## Devices

States:

Registered → personal  
Joined → corporate  
Hybrid joined → AD + Entra  

Joined = full identity control.

---

## Administrative Units (AU)

Because Entra ID is flat, AUs provide scoped delegation.

Use case:
Regional admin manages subset of users.

Important:
Adding group to AU ≠ permissions over members.  
Users must belong to AU.

---

## Licensing & Security Features

Licensing tiers:

P1:
- Conditional Access
- HR provisioning
- SSPR write-back

P2:
- Privileged Identity Management (PIM)
- Identity Protection
- Access reviews

Exam focus:
Know capability categories.

---

## Self-Service Password Reset (SSPR)

Users reset passwords without admin.

Hybrid:
Can write back to AD.

Reduces support dependency.

---

## Roles & Privileges

Two role systems:

Entra ID roles → tenant control  
Azure RBAC roles → resource access  

Example:

Global Admin → tenant  
Contributor → subscription  

Principle:
Least privilege.

---

# Azure Governance Structure

## Management Hierarchy

Azure governance begins at tenant level and scales downward.

Structure:

Management Group  
→ Subscription  
→ Resource Group  
→ Resource  

Root Management Group = top of hierarchy.

---

## Inheritance

Critical concept:

RBAC roles, policies, and budgets assigned at higher levels  
are inherited by all child levels.

Example:

Policy at Management Group  
→ applies to all subscriptions below.

---

## Resource Groups

Logical containers for resources sharing lifecycle.

Lifecycle rule:
Deploy, manage, delete together.

Benefits:

- Access scoping
- Cost tracking
- Application grouping

---

# Governance Guardrails

## Azure Policy

Azure Policy enforces compliance rules (“guardrails”).

Concepts:

Definition → single rule  
Initiative → group of policies  

Common effects:

Audit → report only  
Deny → block creation  
DeployIfNotExists → auto-remediation  

Purpose:
Prevent non-compliant resources.

---

## Resource Locks

Protect resources from accidental change.

Types:

CannotDelete → cannot remove  
ReadOnly → cannot modify  

Important:
Locks affect control plane only, not data plane.

Example:
DB can still store data even if locked.

---

## Tags

Key-value metadata for:

- Billing
- Organization
- Filtering

Important:
Tags do NOT inherit automatically.

Policy can enforce tag inheritance.

---

# Access Control (RBAC)

## RBAC Model

Access = Identity + Role + Scope

Scopes:

Management Group  
Subscription  
Resource Group  
Resource  

Principle:
Least privilege.

---

## Built-in Roles

Owner → full control  
Contributor → manage resources  
Reader → view only  

Custom roles:
Define granular actions if needed.

---

# Cost Management & Optimization

Azure uses consumption-based billing.

Governance ensures financial control.

---

## Cost Analysis

Provides:

- Usage visualization
- Spend forecasts
- Anomaly detection

Used to monitor cost trends.

---

## Budgets & Alerts

Budgets define spending thresholds.

Alerts trigger via Action Groups at:

- Actual spend %
- Forecast spend %

Example:
Alert at 80% of budget.

---

## Cost Optimization Strategies

### Azure Hybrid Benefit
Reuse on-prem licenses in Azure.

### Reservations
1- or 3-year commitment for discount.

### Savings Plans
Flexible compute spend commitment.

---

## Azure Advisor

Recommendation engine for:

- Cost optimization
- Right-sizing
- Idle resource detection
- Security improvements
- Performance tuning

Best practice:
Review weekly.

---

# Governance + Cost Relationship

Governance ensures:

- Policy compliance
- Access control
- Resource organization
- Financial sustainability

Cost management is part of governance.

Goal:
Secure, compliant, financially efficient cloud.