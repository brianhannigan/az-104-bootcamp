# AZ-104 Bootcamp – Day 8  
## Full Review & Scenario Reinforcement (EXAM MODE)

---

# 🔥 Why This Matters

This is where you shift from:

👉 Learning → PASSING THE EXAM

Microsoft does NOT test topics individually anymore.

They test:
- Multi-step scenarios
- Cross-service thinking
- “Best solution” logic

---

# 🧠 Day 8 Objectives

- Combine ALL topics together
- Identify weak areas
- Practice real exam-style scenarios
- Reinforce critical concepts



## 📚 Microsoft Learn Links (Use with Each Section)

- AZ-104 exam prep collection: https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-104
- Build your Azure skills with Learn sandbox: https://learn.microsoft.com/en-us/training/support/faq?pivots=sandbox
- Azure architecture center: https://learn.microsoft.com/en-us/azure/architecture/

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Review Concepts | 2–3 hrs |
| Scenario Labs | 3–4 hrs |
| Practice Questions | 1–2 hrs |

## ⏲️ Day Timer

[▶ Open running timers for this day](../assets/running-timers.html?day=day08)

| Timer | Target |
|---|---|
| Total Day Timer | 8h 00m |

---

# 🔹 STEP 1 – RAPID REVIEW (CRITICAL CONCEPTS)

**⏲️ Session Timer:** 1h 30m

## 🔐 Identity & RBAC

- RBAC = WHO
- Policy = WHAT
- Lock = PROTECTION

---

## 🌐 Networking

- NSG = firewall
- UDR = routing control
- Peering = NOT transitive

---

## 📦 Storage

- Blob vs File vs Disk
- RBAC > SAS > Keys
- Lifecycle = cost savings

---

## 🖥️ Compute

- VM = control
- App Service = managed
- VMSS = scaling

---

## 📊 Monitoring

- Metrics = fast alerts
- Logs = deep analysis
- Log Analytics = required

---

## 📜 Governance

- Policy = enforcement
- Budget = alert only
- Initiative = group policies

---

# 🔥 MUST MEMORIZE (FINAL CORE)

- Lower NSG priority wins
- Peering NOT transitive
- Private Endpoint = private IP
- Availability Set vs Zone
- RBAC vs Policy vs Lock
- Budget does NOT stop spending

---

# 🔹 STEP 2 – SCENARIO LABS (REAL EXAM STYLE)

**⏲️ Session Timer:** 4h 00m

## 🎯 Scenario 1: Secure Storage Access

Requirement:
- Storage must NOT be public
- Only accessible from VNet

👉 Solution:
- Disable public access
- Use Private Endpoint

---

## 🎯 Scenario 2: Prevent Missing Tags

Requirement:
- All resources must have "Environment" tag

👉 Solution:
- Azure Policy (Deny)

---

## 🎯 Scenario 3: Scale Web App Automatically

Requirement:
- Handle traffic spikes automatically

👉 Solution:
- App Service with auto-scale OR VMSS

---

## 🎯 Scenario 4: Route Through Firewall

Requirement:
- All traffic must pass through inspection device

👉 Solution:
- UDR (0.0.0.0/0 → firewall)

---

## 🎯 Scenario 5: High Availability Across Datacenters

Requirement:
- Survive datacenter failure

👉 Solution:
- Availability Zones

---

## 🎯 Scenario 6: Investigate Suspicious Activity

Requirement:
- Query detailed logs

👉 Solution:
- Log Analytics + KQL

---

## 🎯 Scenario 7: Limit Spending Alerts

Requirement:
- Notify when budget exceeded

👉 Solution:
- Budget + Alert

---

# 🔹 STEP 3 – EXAM TRAPS (FINAL ROUND)

**⏲️ Session Timer:** 1h 00m

❌ Trap 1  
Choosing NSG instead of UDR  
👉 NSG = allow/deny  
👉 UDR = routing

---

❌ Trap 2  
Using RBAC instead of Policy  
👉 RBAC ≠ enforcement

---

❌ Trap 3  
Using Public Endpoint when security required  
👉 Private Endpoint

---

❌ Trap 4  
Thinking budget stops cost  
👉 It DOES NOT

---

❌ Trap 5  
Ignoring DNS in connectivity  
👉 Can break everything

---

❌ Trap 6  
Forgetting both NSGs must allow traffic  
👉 Subnet + NIC

---

# 🔹 STEP 4 – PRACTICE QUESTIONS (EXAM STYLE)

**⏲️ Session Timer:** 1h 30m

Q1  
You must block resources without tags.

A. RBAC  
B. Policy (Deny)  
C. NSG  
D. Lock  

Answer: B

---

Q2  
Traffic must pass through firewall:

A. NSG  
B. Policy  
C. UDR  
D. Tag  

Answer: C

---

Q3  
Storage must be internal only:

A. Public endpoint  
B. NSG  
C. Private Endpoint  
D. DNS  

Answer: C

---

Q4  
Auto-scale web app:

A. VM  
B. Disk  
C. App Service / VMSS  
D. Policy  

Answer: C

---

Q5  
Detailed log investigation:

A. Metrics  
B. Logs (Log Analytics)  
C. NSG  
D. RBAC  

Answer: B

---

Q6  
Multiple VNets connected indirectly:

A. Works  
B. Fails (not transitive)  
C. Depends  
D. DNS  

Answer: B

---

Q7  
Budget exceeded:

A. Stops resources  
B. Sends alert  
C. Deletes VM  
D. Blocks user  

Answer: B

---

Q8  
Best secure access to storage:

A. Key  
B. SAS  
C. RBAC  
D. Public  

Answer: C

---

Q9  
Two NSGs applied:

A. One must allow  
B. Both must allow  
C. One denies  
D. DNS decides  

Answer: B

---

Q10  
Prevent deletion of resource:

A. Policy  
B. Lock  
C. RBAC  
D. NSG  

Answer: B

---

# 🧠 FINAL MEMORY CHECK

You should be able to answer instantly:

- What is RBAC vs Policy?  
- When do you use UDR?  
- What is Private Endpoint?  
- Difference between Set vs Zone?  
- Metrics vs Logs?  

---

# 🔁 Reinforcement

Write from memory:

- Scope hierarchy  
- NSG rules  
- Storage types  
- Availability options  

---

# 🚨 Homework (CRITICAL)

1. Rebuild ONE full scenario:
   - VNet
   - VM
   - NSG
   - Storage
   - Policy

2. Break it intentionally

3. Fix it

4. Answer:

👉 What broke first?  
👉 Why?  
👉 How did you fix it?

---

# ⏭️ Next: Day 9 (Full Mock Exam + Weak Area Fix)

- Full test simulation
- Time pressure
- Identify last gaps
