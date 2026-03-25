# AZ-104 FULL MOCK EXAM (REALISTIC)

---

# ⏱️ EXAM RULES

- Questions: 60  
- Time: 90 minutes  
- No notes  
- No pausing  

👉 Target: 80%+

---

# 🔹 QUESTIONS

## SECTION 1 – IDENTITY & GOVERNANCE

Q1  
You need to ensure users can view resources but not modify them.  

A. Owner  
B. Contributor  
C. Reader  
D. Policy  

---

Q2  
You must block resource creation without a required tag.  

A. RBAC  
B. Policy (Deny)  
C. NSG  
D. Lock  

---

Q3  
You need to assign permissions at the lowest level possible.  

A. Management Group  
B. Subscription  
C. Resource Group  
D. Resource  

---

Q4  
User can assign roles but cannot manage resources.  

A. Owner  
B. Contributor  
C. User Access Administrator  
D. Reader  

---

Q5  
You must group multiple policies together.  

A. Tag  
B. Initiative  
C. RBAC  
D. Budget  

---

Q6  
Prevent deletion of a resource.  

A. Policy  
B. Lock  
C. RBAC  
D. NSG  

---

Q7  
Policy effect to automatically fix non-compliant resources.  

A. Deny  
B. Audit  
C. Append  
D. DeployIfNotExists  

---

Q8  
Budget reaches threshold. What happens?  

A. Resources stop  
B. Alert triggers  
C. Deployment blocked  
D. User locked  

---

Q9  
Tags are used for:  

A. Security enforcement  
B. Cost tracking  
C. Network filtering  
D. Identity control  

---

Q10  
RBAC permissions are:  

A. Restrictive  
B. Additive  
C. Blocking  
D. Temporary  

---

## SECTION 2 – NETWORKING

Q11  
Which service filters traffic?  

A. UDR  
B. NSG  
C. Policy  
D. DNS  

---

Q12  
Which controls routing?  

A. NSG  
B. UDR  
C. Tag  
D. RBAC  

---

Q13  
NSG priority:  

A. Higher number wins  
B. Lower number wins  
C. Random  
D. Last created  

---

Q14  
Two NSGs applied (Subnet + NIC).  

A. One must allow  
B. Both must allow  
C. One denies  
D. DNS decides  

---

Q15  
VNet peering is:  

A. Transitive  
B. One-way  
C. Bidirectional  
D. Public  

---

Q16  
Traffic must go through firewall appliance.  

A. NSG  
B. UDR  
C. Policy  
D. Tag  

---

Q17  
Secure internal access to storage.  

A. Public endpoint  
B. NSG  
C. Private Endpoint  
D. DNS  

---

Q18  
Connectivity issue but NSG allows traffic. Likely cause?  

A. Disk  
B. DNS  
C. Tag  
D. RBAC  

---

Q19  
Peering between A-B and B-C. A cannot reach C. Why?  

A. NSG  
B. DNS  
C. Not transitive  
D. Policy  

---

Q20  
Public internet access requires:  

A. Private IP  
B. Public IP  
C. Subnet  
D. DNS  

---

## SECTION 3 – STORAGE

Q21  
Best storage for images and videos:  

A. File  
B. Disk  
C. Blob  
D. Queue  

---

Q22  
Shared file system across VMs:  

A. Blob  
B. File  
C. Disk  
D. Archive  

---

Q23  
VM storage:  

A. Blob  
B. File  
C. Disk  
D. Queue  

---

Q24  
Most secure access method:  

A. Key  
B. SAS  
C. RBAC  
D. Public  

---

Q25  
Temporary access:  

A. RBAC  
B. SAS  
C. Key  
D. Policy  

---

Q26  
Replication across regions:  

A. LRS  
B. ZRS  
C. GRS  
D. Hot  

---

Q27  
Read access to secondary region:  

A. GRS  
B. RA-GRS  
C. ZRS  
D. LRS  

---

Q28  
Cheapest storage tier:  

A. Hot  
B. Cool  
C. Archive  
D. Premium  

---

Q29  
Reduce cost automatically:  

A. NSG  
B. Policy  
C. Lifecycle  
D. DNS  

---

Q30  
Secure storage from internet:  

A. NSG  
B. Public endpoint  
C. Private Endpoint  
D. Tag  

---

## SECTION 4 – COMPUTE

Q31  
Need full OS control:  

A. App Service  
B. VM  
C. Disk  
D. Function  

---

Q32  
Web app with minimal management:  

A. VM  
B. App Service  
C. Disk  
D. NSG  

---

Q33  
Auto-scale compute:  

A. VM  
B. VMSS  
C. Disk  
D. NSG  

---

Q34  
High availability across datacenters:  

A. Availability Set  
B. Availability Zone  
C. NSG  
D. Policy  

---

Q35  
Same datacenter protection:  

A. Set  
B. Zone  
C. Policy  
D. NSG  

---

Q36  
Multiple apps share compute:  

A. VM  
B. Disk  
C. App Service Plan  
D. RBAC  

---

Q37  
Cheapest disk type:  

A. Premium SSD  
B. Standard SSD  
C. Standard HDD  
D. ZRS  

---

Q38  
App Service manages:  

A. Network  
B. OS  
C. Disk  
D. RBAC  

---

Q39  
Scaling manually is bad practice. Use:  

A. NSG  
B. VMSS  
C. Tag  
D. Policy  

---

Q40  
App Service vs VM difference:  

A. Cost  
B. OS control  
C. Storage  
D. DNS  

---

## SECTION 5 – MONITORING

Q41  
Where are logs stored?  

A. VM  
B. Log Analytics  
C. NSG  
D. Disk  

---

Q42  
Fast alerts:  

A. Logs  
B. Metrics  
C. NSG  
D. RBAC  

---

Q43  
Query logs:  

A. SQL  
B. PowerShell  
C. KQL  
D. Bash  

---

Q44  
Alert without action group:  

A. Works  
B. No notification  
C. Fails  
D. Blocks  

---

Q45  
Backup requires:  

A. NSG  
B. Vault  
C. Tag  
D. Policy  

---

Q46  
Detailed investigation:  

A. Metrics  
B. Logs  
C. Disk  
D. NSG  

---

Q47  
Send alert email:  

A. Action Group  
B. Policy  
C. RBAC  
D. Tag  

---

Q48  
Retention affects:  

A. Security  
B. Cost  
C. Network  
D. DNS  

---

Q49  
Monitor is:  

A. SIEM  
B. Base monitoring  
C. Firewall  
D. Storage  

---

Q50  
Sentinel is:  

A. Storage  
B. SIEM  
C. NSG  
D. Disk  

---

## SECTION 6 – MIXED SCENARIOS

Q51  
Enforce compliance:  

A. RBAC  
B. Policy  
C. NSG  
D. Tag  

---

Q52  
Route traffic:  

A. NSG  
B. UDR  
C. Policy  
D. Lock  

---

Q53  
Prevent deletion:  

A. Policy  
B. Lock  
C. RBAC  
D. NSG  

---

Q54  
Secure internal access:  

A. Public endpoint  
B. Private Endpoint  
C. NSG  
D. DNS  

---

Q55  
Investigate logs:  

A. Metrics  
B. Log Analytics  
C. RBAC  
D. Disk  

---

Q56  
Scale automatically:  

A. VM  
B. VMSS  
C. Disk  
D. NSG  

---

Q57  
Temporary storage access:  

A. RBAC  
B. SAS  
C. Key  
D. Policy  

---

Q58  
Block non-compliant resource:  

A. RBAC  
B. Policy  
C. NSG  
D. Tag  

---

Q59  
Allow/deny traffic:  

A. NSG  
B. UDR  
C. Policy  
D. Lock  

---

Q60  
Best secure access:  

A. Key  
B. SAS  
C. RBAC  
D. Public  

---

# 🔹 ANSWER KEY

1:C 2:B 3:D 4:C 5:B 6:B 7:D 8:B 9:B 10:B  
11:B 12:B 13:B 14:B 15:C 16:B 17:C 18:B 19:C 20:B  
21:C 22:B 23:C 24:C 25:B 26:C 27:B 28:C 29:C 30:C  
31:B 32:B 33:B 34:B 35:A 36:C 37:C 38:B 39:B 40:B  
41:B 42:B 43:C 44:B 45:B 46:B 47:A 48:B 49:B 50:B  
51:B 52:B 53:B 54:B 55:B 56:B 57:B 58:B 59:A 60:C  

---

# 🎯 SCORING

| Score | Status |
|------|--------|
| 90–100% | READY |
| 80–89% | VERY CLOSE |
| 70–79% | REVIEW WEAK AREAS |
| <70% | REPEAT DAYS |

---

# 🚨 NEXT STEP

- Calculate your score  
- Tell me your weak areas  

👉 I will fix them FAST
