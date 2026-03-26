
RBAC Analysis


Resource analyzed: Cyber-Range-VNet (Azure Virtual Network)


>


Focus: How it was built, why it exists, what we can infer, and where it can be improved.




1. What This Is (Context)
This document reverse-engineers the Azure Virtual Network (VNet) named Cyber-Range-VNet, based on its Access Control (IAM) configuration viewed in the Azure Portal.
The analysis is intentionally architecture-focused, not just descriptive. The goal is to understand:

What exists
Why it likely exists
How it was probably built
Where improvements can be made
The screenshot shows RBAC assignments scoped directly to the Virtual Network, not the subscription or entire resource group.


2. High-Level Purpose (The “Why”)
Based on naming and RBAC patterns, this environment is almost certainly a cyber range or security lab.
Likely use cases

Cybersecurity training
Student labs
Blue team / red team exercises
Incident response simulations
Safe experimentation with risky configurations
Evidence supporting this

The resource name: Cyber-Range-VNet
Presence of student-oriented access (e.g., Student Subnet Joiner)
A large number of Reader assignments
VM login roles instead of broad VM control
Defender for Cloud–related roles
Log Analytics access assigned separately
This is not a minimal or ad-hoc VNet; it is intentionally designed.


3. What We See in IAM (RBAC Breakdown)
The VNet has roughly 40 role assignments, including:
Core administrative roles

Owner (3)
Contributor (6)
User Access Administrator (3)
Role Based Access Control Administrator (2)
Read-only / visibility roles

Reader (12)
Compute-related roles

Virtual Machine Contributor (2)
Virtual Machine User Login (2)
Monitoring & security roles

Log Analytics Contributor (2)
Security Admin (1)
Defender Agentless VM Scan (1)
Defender Kubernetes API Access (1)
Storage & eventing roles

Storage Account Contributor (2)
Storage Blob Data Reader (1)
EventGrid Contributor (1)
Specialized / custom roles

Student Subnet Joiner (1) (likely custom)


4. How This Was Likely Built (Probable Build Sequence)
4.1 Subscription & Resource Groups
The environment likely started with:

A dedicated subscription (or a clearly segmented shared one)
Networking resources isolated into a specific resource group
RBAC at the subscription level was probably kept tight, pushing permissions downward to specific scopes.


4.2 Virtual Network Design
The Cyber-Range-VNet likely contains multiple subnets, such as:

Student workload subnets
Instructor / admin subnets
Security tooling subnets
Jumpbox / Bastion subnet
Subnet separation supports containment, control, and repeatable lab scenarios.


4.3 RBAC Scoped at the VNet Level
Instead of giving broad access at the subscription or resource-group level, permissions were assigned directly to the Virtual Network.
This enables:

Fine-grained networking control
Reduced blast radius
More realistic enterprise-style permission modeling
This is an advanced and intentional decision.


4.4 Custom Role Usage (Key Signal)
The presence of Student Subnet Joiner strongly suggests a custom RBAC role.
That role likely allows:

Microsoft.Network/virtualNetworks/subnets/join/action
And explicitly does not allow:

Creating or deleting VNets
Modifying NSGs or route tables
Changing address spaces
This allows students to attach NICs to approved subnets without broader control — an excellent least‑privilege example.


4.5 Monitoring & Security Integration
Roles tied to Defender and Log Analytics indicate:

Microsoft Defender for Cloud is enabled
Activity and telemetry are being collected
Security visibility matters in this environment
This aligns perfectly with cyber range objectives.


5. What This Design Does Well
✅ Principle of Least Privilege
Permissions are scoped narrowly and purposefully, rather than defaulting to Owner or Contributor everywhere.


✅ Clear Persona Separation
Distinct access patterns exist for:

Students
Instructors
Security personnel
Platform administrators
This mirrors real-world enterprise environments.


✅ Network-Level Control
Applying RBAC at the VNet (and likely subnet) level avoids dangerous, overly broad permissions.


✅ Observability Built-In
Monitoring and Defender roles ensure the environment is observable and auditable — critical for training and security work.


6. Recommended Improvements
Even strong designs can improve.
6.1 Reduce Owner Assignments
Current: 3 Owners
Risk:

Any Owner can delete the VNet
Harder to audit accountability
Recommendation:

Reduce to 1 Owner
Use Contributor + User Access Administrator for others


6.2 Favor Managed Identities for Tooling
Some roles (EventGrid, Defender, Log Analytics) may belong to:

Automation
Security tooling
Pipelines
Recommendation:

Assign these roles to Managed Identities, not human users


6.3 Review Reader Sprawl
While Reader seems harmless, it exposes:

Network topology
IP ranges
Security architecture
Recommendation:

Confirm all 12 Readers truly need visibility
Narrow scope to resource group or specific resources where possible


6.4 Document RBAC Intentionally
This environment would strongly benefit from a documented RBAC matrix.
Example:

Persona → Role → Scope → Purpose
This both improves security and makes the environment a teaching tool.


6.5 Azure Policy (If Not Already Used)
Highly recommended policies for a cyber range:

Restrict public IP creation
Enforce approved VM images
Limit VM sizes
Enforce auto-shutdown schedules
These prevent accidents without removing learning value.


7. Key Takeaway
This is a deliberately designed, security-aware Azure networking environment.
It demonstrates:

Enterprise-grade RBAC usage
Clear intent around training and experimentation
Strong separation of concerns
It is an excellent environment to learn from, especially if you want real-world Azure architecture experience.


8. Open Questions / Next Steps
To deepen understanding and improve documentation, possible next steps include:

Mapping one complete student workflow (identity → role → action)
Deep analysis of the custom RBAC role(s)
Reviewing NSGs, route tables, and firewalls
Creating a logical architecture diagram (network + identity)
Reviewing subscription- and resource-group-level RBAC inheritance


