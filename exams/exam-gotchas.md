# AZ-104 – EXAM GOTCHAS (CRITICAL LAST-MINUTE REVIEW)

---

# 🔥 WHY THIS EXISTS

These are the mistakes that cause:
👉 70% → FAIL  
👉 80% → PASS  

Microsoft LOVES testing confusion.

---

# 🔹 IDENTITY & RBAC GOTCHAS

❌ Trap 1  
RBAC vs Policy confusion  
👉 RBAC = WHO has access  
👉 Policy = WHAT is allowed  

---

❌ Trap 2  
Assigning roles too high  
👉 Always choose LOWEST scope possible  

---

❌ Trap 3  
Permissions not working  
👉 RBAC is **additive**, not restrictive  

---

❌ Trap 4  
Owner still blocked  
👉 Locks override RBAC  

---

❌ Trap 5  
User Access Administrator misunderstood  
👉 Can assign roles, NOT manage resources  

---

# 🔹 NETWORKING GOTCHAS (BIGGEST FAIL AREA)

❌ Trap 6  
NSG vs UDR confusion  
👉 NSG = allow/deny  
👉 UDR = route traffic  

---

❌ Trap 7  
NSG priority backwards  
👉 LOWER number = HIGHER priority  

---

❌ Trap 8  
Two NSGs applied  
👉 BOTH must allow traffic  

---

❌ Trap 9  
Peering assumed transitive  
👉 IT IS NOT  

---

❌ Trap 10  
Connectivity issue blamed on NSG  
👉 Could be DNS  

---

❌ Trap 11  
Forcing traffic through firewall  
👉 MUST use UDR  

---

❌ Trap 12  
Public vs Private access  
👉 Secure = Private Endpoint  

---

# 🔹 STORAGE GOTCHAS

❌ Trap 13  
Blob vs File confusion  
👉 Blob = object  
👉 File = shared drive  

---

❌ Trap 14  
Using Access Keys  
👉 Always choose RBAC first  

---

❌ Trap 15  
Redundancy misunderstanding  
👉 ZRS = zones  
👉 GRS = region  

---

❌ Trap 16  
Need read from secondary  
👉 RA-GRS  

---

❌ Trap 17  
Cost optimization ignored  
👉 Lifecycle policies  

---

❌ Trap 18  
Public access accidentally enabled  
👉 Disable it unless required  

---

# 🔹 COMPUTE GOTCHAS

❌ Trap 19  
Using VM instead of App Service  
👉 Web app = App Service  

---

❌ Trap 20  
Availability Set vs Zone  
👉 Set = same datacenter  
👉 Zone = different datacenters  

---

❌ Trap 21  
Scaling manually  
👉 Use VMSS  

---

❌ Trap 22  
App Service OS confusion  
👉 Azure manages OS  

---

❌ Trap 23  
Multiple apps → multiple plans  
👉 Can share ONE App Service Plan  

---

# 🔹 MONITORING GOTCHAS

❌ Trap 24  
Metrics vs Logs confusion  
👉 Metrics = alerts  
👉 Logs = investigation  

---

❌ Trap 25  
Querying logs without workspace  
👉 Need Log Analytics  

---

❌ Trap 26  
Alert without action  
👉 No Action Group = no notification  

---

❌ Trap 27  
Backup without vault  
👉 NOT possible  

---

❌ Trap 28  
Sentinel vs Monitor confusion  
👉 Sentinel = SIEM  
👉 Monitor = base platform  

---

# 🔹 GOVERNANCE GOTCHAS

❌ Trap 29  
Tags enforce rules  
👉 THEY DO NOT  

---

❌ Trap 30  
Budget stops spending  
👉 It DOES NOT  

---

❌ Trap 31  
Multiple policies separately  
👉 Use Initiative  

---

❌ Trap 32  
Wrong policy effect  
👉 Deny vs Audit vs DeployIfNotExists  

---

❌ Trap 33  
Trying to fix with RBAC  
👉 Policy is enforcement tool  

---

# 🔹 CROSS-TOPIC GOTCHAS (VERY IMPORTANT)

❌ Trap 34  
“Secure access”  
👉 Private Endpoint  

---

❌ Trap 35  
“Enforce compliance”  
👉 Policy  

---

❌ Trap 36  
“Route traffic”  
👉 UDR  

---

❌ Trap 37  
“Allow or block traffic”  
👉 NSG  

---

❌ Trap 38  
“Scale automatically”  
👉 VMSS or App Service  

---

❌ Trap 39  
“Investigate logs”  
👉 Log Analytics  

---

❌ Trap 40  
“Prevent deletion”  
👉 Lock  

---

# 🔥 FINAL MEMORY RULES

You should instantly know:

- RBAC vs Policy vs Lock  
- NSG vs UDR  
- Blob vs File vs Disk  
- Set vs Zone  
- Metrics vs Logs  
- Private Endpoint  

---

# 🚨 FINAL WARNING

If TWO answers look correct:

👉 Choose the one that is:
- MORE secure  
- MORE automated  
- LESS manual work  

---

# 🧠 FINAL CHECK

If you hesitate on ANY of these:
👉 Review that section BEFORE exam

---

# 🎯 THIS IS YOUR EDGE

Most people FAIL because of:
- Confusion  
- Overthinking  
- Misreading  

You PASS by:
- Recognizing patterns  
- Eliminating wrong answers FAST  
- Trusting these rules  

---

# 🚀 YOU ARE READY
