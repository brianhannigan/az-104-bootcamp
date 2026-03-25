# AZ-104 Bootcamp – Day 1  
## Identity, RBAC, and Governance (Exam-Focused)

---

# 🔥 Updated Strategy (Based on Background)

You already have:
- Defender + Sentinel exposure ✅
- Some Azure exposure ✅
- PowerShell + CLI comfort ✅

### Focus Areas
- 🔴 Networking (critical gap)
- 🔴 Storage nuances
- 🔴 RBAC + Policy edge cases
- 🔴 Scenario-based thinking

---

# 🧠 Day 1 Objectives

- Microsoft Entra (Identity basics)
- RBAC (Roles + Scope + Inheritance)
- Resource organization (RGs, Subscriptions)
- Azure Policy
- Locks
- Tags
- Cost basics

---


## 📚 Microsoft Learn Links (Use with Each Section)

- Identity + Governance learning path (AZ-104 aligned): https://learn.microsoft.com/en-us/training/paths/preparing-for-az-104-manage-azure-identities-and-governance-1-of-5/
- Azure RBAC module (hands-on): https://learn.microsoft.com/en-us/training/modules/secure-azure-resources-with-rbac/
- Azure Policy module: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-policy/

---
# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

## ⏲️ Day Timer

[▶ Open running timers for this day](../assets/running-timers.html?day=day01)

| Timer | Target |
|---|---|
| Total Day Timer | 8h 00m |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

**⏲️ Session Timer:** 2h 00m

## 🧩 Azure Hierarchy

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/governance/management-groups/overview


Management Group  
↓  
Subscription  
↓  
Resource Group  
↓  
Resource  

- Permissions flow **downward**
- Always assign at **lowest scope possible**

---

## 🔐 RBAC (Role-Based Access Control)

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/role-based-access-control/overview


### 🔥 MOST TESTED
RBAC = **Who can do what, where**

| Component | Meaning |
|----------|--------|
| Who | User / Group |
| What | Role |
| Where | Scope |

---

## 🔑 Built-in Roles

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles


| Role | Can Do | Cannot Do |
|------|--------|----------|
| Reader | View | No changes |
| Contributor | Manage resources | Cannot assign roles |
| Owner | Full control | — |
| User Access Admin | Manage RBAC | No resource control |

---

## ⚠️ RBAC Rules

📘 Microsoft Learn (scope/inheritance): https://learn.microsoft.com/en-us/azure/role-based-access-control/scope-overview


- Permissions are **additive**
- Higher scope → inherits downward
- Always use **least privilege**

---

## 🧠 RBAC Example

User has:
- Reader @ Subscription  
- Contributor @ Resource Group  

👉 Result: **Contributor wins at RG**

---

## 🛑 Locks

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/lock-resources


| Lock | Effect |
|------|-------|
| CanNotDelete | Cannot delete |
| ReadOnly | Cannot modify or delete |

🔥 Locks override RBAC

---

## 📜 Azure Policy

📘 Microsoft Learn: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-policy/


| Feature | Purpose |
|--------|--------|
| RBAC | WHO can access |
| Policy | WHAT is allowed |

Examples:
- Require tags → Policy
- Restrict region → Policy

---

## 🏷️ Tags

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/tag-resources


Used for:
- Cost tracking
- Organization

⚠️ Tags DO NOT enforce rules → Policy does

---

## 🏢 Management Groups

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/governance/management-groups/overview


Use when:
- Applying rules across multiple subscriptions

---

## 💰 Cost Basics

📘 Microsoft Learn: https://learn.microsoft.com/en-us/azure/cost-management-billing/cost-management-billing-overview


Know:
- Budgets
- Alerts
- Azure Advisor

---

# Azure AD Quick Add

## Azure AD Join Types

📘 Microsoft Learn: https://learn.microsoft.com/en-us/entra/identity/devices/overview


| Type | Description |
|------|------------|
| Azure AD Join | Cloud-only devices |
| Hybrid Join | On-prem + Azure |
| Registered | Personal devices |

---

## SSPR

📘 Microsoft Learn: https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-sspr


- Allows users to reset password without admin
- Requires authentication methods configured

---

## Guest Users

📘 Microsoft Learn: https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b


- External users (B2B)
- Limited access

# 🔹 STEP 2 – HANDS-ON LAB

**⏲️ Session Timer:** 3h 30m

## 🎯 Scenario

📘 Microsoft Learn lab support:
- Create and manage resource groups: https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal
- Assign Azure roles: https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal
- Create policy assignments: https://learn.microsoft.com/en-us/azure/governance/policy/assign-policy-portal


You must:
- Create RG
- Create group
- Assign RBAC
- Enforce tags
- Prevent deletion

---

## 🔧 Portal Steps

### 1. Create Resource Group
Name: rg-day1-core

---

### 2. Create Group
Name: vm-operators

---

### 3. Assign RBAC
Role: Contributor  
Scope: Resource Group

---

### 4. Add Lock
Type: CanNotDelete

---

### 5. Apply Policy
Require tag: Environment

---

### 6. Test Policy
Try creating resource WITHOUT tag  
👉 Should fail

---

# 💻 CLI Commands

az group create --name rg-day1-core --location eastus

az lock create \
  --name no-delete \
  --lock-type CanNotDelete \
  --resource-group rg-day1-core

az lock list --resource-group rg-day1-core --output table

---

# 💻 PowerShell Commands

Connect-AzAccount

New-AzResourceGroup -Name "rg-day1-core" -Location "EastUS"

New-AzResourceLock `
  -LockName "no-delete" `
  -LockLevel CanNotDelete `
  -ResourceGroupName "rg-day1-core"

---

# 🔹 STEP 3 – EXAM TRAPS

**⏲️ Session Timer:** 45m

❌ Trap 1  
User blocked despite Contributor  
👉 Policy restriction

❌ Trap 2  
Owner cannot delete  
👉 Lock exists

❌ Trap 3  
Multiple subscriptions  
👉 Management Group

❌ Trap 4  
Require tags  
👉 Policy, NOT tags

❌ Trap 5  
Minimize permissions  
👉 Lowest scope + least role

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

**⏲️ Session Timer:** 1h 45m

Q1  
User must create VMs but NOT assign roles.

A. Owner  
B. Contributor  
C. Reader  
D. Policy Contributor  

Answer: B

---

Q2  
Reader @ Subscription + Contributor @ RG

Result?

A. Read only  
B. Full control  
C. Contributor  
D. No access  

Answer: C

---

Q3  
Require tag on all resources

A. RBAC  
B. Tag  
C. Policy  
D. Lock  

Answer: C

---

Q4  
Owner cannot delete resource

A. NSG  
B. Policy  
C. Lock  
D. Subscription  

Answer: C

---

Q5  
Same rules across subscriptions

A. RG  
B. RBAC  
C. Management Group  
D. Tag  

Answer: C

---

Q6  
Overrides RBAC?

A. Tag  
B. Policy  
C. Lock  
D. Both B and C  

Answer: D

---

Q7  
Access to only one VM

A. Subscription  
B. RG  
C. Resource  
D. Management Group  

Answer: C

---

# 🧠 MUST MEMORIZE

- Scope order:
  Management Group → Subscription → Resource Group → Resource

- RBAC = WHO  
- Policy = WHAT  
- Lock = PROTECTION  

- Reader = view  
- Contributor = manage  
- Owner = everything  

---

# 🔁 Reinforcement

Repeat from memory:
- Scope hierarchy
- RBAC vs Policy vs Lock
- Role differences

---

# 🚨 Homework

1. Complete lab (portal + CLI)
2. Break it intentionally:
   - Try deleting locked resource
   - Try creating resource without tag

3. Answer:
   - What failed?
   - WHY?

---

# ⏭️ Next: Day 2 (Networking – CRITICAL)

Topics:
- VNets
- Subnets
- NSGs
- Routing
- Peering
