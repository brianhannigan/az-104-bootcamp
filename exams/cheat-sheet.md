# AZ-104 FINAL CHEAT SHEET (BRAIN DUMP)

---

# 🔥 CORE RULES (MEMORIZE FIRST)

- RBAC = WHO  
- Policy = WHAT  
- Lock = PROTECTION  

- NSG = FILTER traffic  
- UDR = ROUTE traffic  

- Private Endpoint = PRIVATE IP access  

- Metrics = ALERTS  
- Logs = INVESTIGATION  

- Budget = ALERT ONLY (does NOT stop spend)

---

# 🔐 IDENTITY & GOVERNANCE

## Scope Hierarchy
Management Group → Subscription → Resource Group → Resource

👉 Permissions flow DOWN

---

## RBAC Roles

| Role | What It Does |
|------|-------------|
| Reader | View only |
| Contributor | Manage resources |
| Owner | Full control |
| User Access Admin | Assign roles only |

---

## Policy Effects

| Effect | Meaning |
|--------|--------|
| Deny | Block |
| Audit | Log |
| Append | Add |
| DeployIfNotExists | Auto-fix |

---

## Locks

| Lock | Effect |
|------|-------|
| CanNotDelete | No delete |
| ReadOnly | No changes |

🔥 Locks override RBAC

---

# 🌐 NETWORKING

## Core Flow

Internet → Public IP → NSG → Subnet → VM

---

## NSG Rules

- Lower priority number = higher priority  
- First match wins  

🔥 Subnet + NIC NSG → BOTH must allow

---

## UDR (Routing)

- Overrides default routing  
- Used for firewalls  

👉 0.0.0.0/0 = all traffic

---

## VNet Peering

- Private connection  
- NOT transitive  
- Must be configured BOTH ways  

---

## Public vs Private

| Type | Purpose |
|------|--------|
| Public IP | Internet |
| Private IP | Internal |

---

## DNS

👉 If DNS fails → connectivity fails

---

# 📦 STORAGE

## Types

| Type | Use |
|------|-----|
| Blob | Object (images, logs) |
| File | Shared drive |
| Disk | VM storage |

---

## Redundancy

| Type | Meaning |
|------|--------|
| LRS | Local |
| ZRS | Zones |
| GRS | Region |
| RA-GRS | Read secondary |

---

## Access Methods

| Method | Priority |
|--------|---------|
| RBAC | BEST |
| SAS | Temporary |
| Keys | Avoid |

---

## Tiers

| Tier | Use |
|------|-----|
| Hot | Frequent |
| Cool | Less |
| Archive | Rare |

---

## Lifecycle

👉 Move data automatically to reduce cost

---

# 🖥️ COMPUTE

## VM vs App Service

| Feature | VM | App Service |
|--------|---|------------|
| OS control | Yes | No |
| Maintenance | You | Azure |

---

## Availability

| Type | Meaning |
|------|--------|
| Set | Same DC |
| Zone | Different DC |

---

## Scaling

👉 VMSS = auto-scale  
👉 App Service = built-in scaling  

---

## Disks

| Type | Cost |
|------|------|
| HDD | Cheapest |
| SSD | Medium |
| Premium | Fastest |

---

# 📊 MONITORING

## Azure Monitor

👉 Central monitoring system

---

## Metrics vs Logs

| Metrics | Logs |
|--------|------|
| Fast | Detailed |
| Alerts | Investigation |

---

## Log Analytics

👉 Required for KQL queries

---

## Alerts Flow

Condition → Alert → Action Group → Notification

---

## Backup

👉 Requires Recovery Services Vault  

---

# 📜 GOVERNANCE & COST

## Key Rules

- Policy enforces  
- Tags organize  
- Budget alerts only  

---

## Cost Tools

| Tool | Use |
|------|-----|
| Budget | Alerts |
| Advisor | Recommendations |
| Cost Analysis | Breakdown |

---

## Initiatives

👉 Group policies together

---

# 🔥 “IF YOU SEE THIS → ANSWER THIS”

| Keyword | Answer |
|--------|--------|
| Enforce | Policy |
| Secure internal | Private Endpoint |
| Route traffic | UDR |
| Allow/Deny | NSG |
| Scale | VMSS / App Service |
| Query logs | Log Analytics |
| Temporary access | SAS |
| Prevent delete | Lock |
| Multi-policy | Initiative |

---

# 🚨 FINAL TRAPS

- RBAC ≠ Policy  
- NSG ≠ Routing  
- Peering ≠ Transitive  
- Budget ≠ Stop spending  
- Tags ≠ Enforcement  
- Metrics ≠ Logs  

---

# 🧠 FINAL MEMORY

Say this out loud:

- RBAC = WHO  
- Policy = WHAT  
- NSG = FILTER  
- UDR = ROUTE  
- Private Endpoint = SECURE  

---

# 🎯 EXAM STRATEGY

1. Read LAST sentence first  
2. Identify keyword  
3. Eliminate wrong answers  
4. Choose MOST secure / least effort  

---

# 🏁 YOU ARE READY

# AZ-104 Cheat Sheet

## Governance

- RBAC = who can do what
- Policy = what is allowed
- Lock = protection
- Tags = organization

## Scope Order

Management Group â†’ Subscription â†’ Resource Group â†’ Resource

## Networking

- VNet = network boundary
- Subnet = segmented network
- NSG = traffic filter
- UDR = routing override
- Peering = private VNet connection

## Storage

- Blob = object storage
- File = SMB/NFS share
- Disk = VM disk storage
- Hot/Cool/Archive = access tiers

## Compute

- Availability Set = fault/update domain protection
- Availability Zone = datacenter-level separation
- VMSS = scalable VM group

## Monitoring

- Metrics = numeric time-series data
- Logs = detailed records
- Alerts = notification/action trigger
