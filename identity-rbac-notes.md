# Day 2 — Azure Identity and RBAC

## What is RBAC
Role-Based Access Control (RBAC) controls who can do what in Azure and where.

It is based on:
- Identity (user or group)
- Role (permissions)
- Scope (where access applies)

## What is a Role
A role defines allowed actions.

Examples:
- Reader → can view resources
- Contributor → can create and modify
- Owner → full control

## What is Scope
Scope defines where the role applies.

Levels:
- Management group
- Subscription
- Resource group
- Resource

## What I did in this lab
- Created a resource group: az104-identity-rg
- Created Entra ID group: az104-rbac-readers
- Assigned Reader role to the group on the resource group
- Verified role assignment
- Deleted resources

## Key understanding
Permissions in Azure are assigned to identities at specific scopes using roles.