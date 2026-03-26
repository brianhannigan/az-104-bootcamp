# RBAC Analysis: Cyber-Range-VNet

**Resource analyzed:** `Cyber-Range-VNet` (Azure Virtual Network)

**Focus:** How it was built, why it exists, what we can infer, and where it can be improved.

## 1) What This Is (Context)

This document reverse-engineers the Azure Virtual Network (VNet) named `Cyber-Range-VNet` based on its Access Control (IAM) configuration viewed in the Azure Portal.

The analysis is architecture-focused (not just descriptive). The goal is to understand:

- What exists
- Why it likely exists
- How it was probably built
- Where improvements can be made

> The screenshot shows RBAC assignments scoped directly to the Virtual Network, not the subscription or entire resource group.

## 2) High-Level Purpose (The “Why”)

Based on naming and RBAC patterns, this environment is almost certainly a cyber range or security lab.

### Likely use cases

- Cybersecurity training
- Student labs
- Blue team / red team exercises
- Incident response simulations
- Safe experimentation with risky configurations

### Evidence supporting this

- The resource name: `Cyber-Range-VNet`
- Presence of student-oriented access (for example, `Student Subnet Joiner`)
- A large number of `Reader` assignments
- VM login roles instead of broad VM control
- Defender for Cloud–related roles
- Log Analytics access assigned separately

This is not a minimal or ad-hoc VNet; it appears intentionally designed.

## 3) What We See in IAM (RBAC Breakdown)

The VNet has roughly **40** role assignments, including:

### Core administrative roles

- Owner (3)
- Contributor (6)
- User Access Administrator (3)
- Role Based Access Control Administrator (2)

### Read-only / visibility roles

- Reader (12)

### Compute-related roles

- Virtual Machine Contributor (2)
- Virtual Machine User Login (2)

### Monitoring & security roles

- Log Analytics Contributor (2)
- Security Admin (1)
- Defender Agentless VM Scan (1)
- Defender Kubernetes API Access (1)

### Storage & eventing roles

- Storage Account Contributor (2)
- Storage Blob Data Reader (1)
- EventGrid Contributor (1)

### Specialized / custom roles

- Student Subnet Joiner (1) *(likely custom)*

## 4) How This Was Likely Built (Probable Build Sequence)

### 4.1) Subscription & resource groups

The environment likely started with:

- A dedicated subscription (or a clearly segmented shared one)
- Networking resources isolated into a specific resource group
- Tight subscription-level RBAC, with targeted permissions applied at narrower scopes

### 4.2) Virtual network design

`Cyber-Range-VNet` likely contains multiple subnets, such as:

- Student workload subnets
- Instructor / admin subnets
- Security tooling subnets
- Jumpbox / Bastion subnet

Subnet separation supports containment, control, and repeatable lab scenarios.

### 4.3) RBAC scoped at the VNet level

Instead of broad access at subscription or resource-group scope, permissions were assigned directly to the VNet.

This enables:

- Fine-grained networking control
- Reduced blast radius
- More realistic enterprise-style permission modeling

This appears to be an advanced, intentional choice.

### 4.4) Custom role usage (key signal)

The presence of `Student Subnet Joiner` strongly suggests a custom RBAC role.

That role likely allows:

- `Microsoft.Network/virtualNetworks/subnets/join/action`

And likely does **not** allow:

- Creating or deleting VNets
- Modifying NSGs or route tables
- Changing address spaces

This allows students to attach NICs to approved subnets without broader control, which is a strong least-privilege pattern.

### 4.5) Monitoring & security integration

Roles tied to Defender and Log Analytics indicate:

- Microsoft Defender for Cloud is enabled
- Activity and telemetry are being collected
- Security visibility is important in this environment

This strongly aligns with cyber range objectives.

## 5) What This Design Does Well

- ✅ **Principle of least privilege:** Permissions appear scoped narrowly and purposefully instead of defaulting to Owner/Contributor everywhere.
- ✅ **Clear persona separation:** Distinct access patterns appear to exist for students, instructors, security personnel, and platform administrators.
- ✅ **Network-level control:** Applying RBAC at VNet (and likely subnet) scope avoids dangerous broad permissions.
- ✅ **Observability built in:** Monitoring and Defender roles support auditability and incident analysis.

## 6) Recommended Improvements

Even strong designs can improve.

### 6.1) Reduce Owner assignments

**Current:** 3 Owners
**Risk:** Any Owner can delete the VNet and dilute accountability.

**Recommendation:**

- Reduce to 1 Owner where possible
- Use Contributor + User Access Administrator for other admin personas

### 6.2) Favor Managed Identities for tooling

Some roles (EventGrid, Defender, Log Analytics) may belong to automation or platform tooling.

**Recommendation:**

- Assign these roles to Managed Identities rather than human users

### 6.3) Review Reader sprawl

`Reader` seems harmless but can expose:

- Network topology
- IP ranges
- Security architecture

**Recommendation:**

- Confirm all 12 Reader assignments are necessary
- Narrow scope to resource groups or specific resources where possible

### 6.4) Document RBAC intentionally

This environment would benefit from a documented RBAC matrix, for example:

- Persona → Role → Scope → Purpose

This improves both security posture and training value.

### 6.5) Apply Azure Policy guardrails (if not already used)

Recommended policy controls for cyber ranges:

- Restrict public IP creation
- Enforce approved VM images
- Limit VM sizes
- Enforce auto-shutdown schedules

These controls prevent accidental misconfiguration without removing learning value.

## 7) Key Takeaway

This appears to be a deliberately designed, security-aware Azure networking environment.

It demonstrates:

- Enterprise-grade RBAC patterns
- Clear intent around training and experimentation
- Strong separation of concerns

It is an excellent environment to learn from for real-world Azure architecture practices.

## 8) Open Questions / Next Steps

To deepen understanding and improve documentation, potential next steps include:

- Map one complete student workflow (identity → role → action)
- Validate subnet-level RBAC and NSG boundaries
- Inventory inherited vs. directly assigned roles
- Tie each role assignment to an explicit operational requirement
