# Day 1 â€“ Identity, RBAC, Governance

## Objectives

- Understand Azure hierarchy
- Learn RBAC roles and scopes
- Understand Policy, Locks, and Tags
- Build a simple governance lab

## Key Concepts

- Management Group â†’ Subscription â†’ Resource Group â†’ Resource
- RBAC = who can do what
- Policy = what is allowed
- Lock = protection from modification or deletion
- Tags = organization and reporting

## Hands-On Lab

1. Create a resource group
2. Create a test group
3. Assign Contributor at RG scope
4. Add a CanNotDelete lock
5. Assign a tag policy

## Exam Traps

- Locks override normal delete operations
- Policy can block deployment
- Tags alone do not enforce compliance
- Contributor cannot assign RBAC roles

## Review Questions

1. What is the difference between RBAC and Policy?
2. What is the difference between Contributor and Owner?
3. Why would you use a lock instead of changing permissions?