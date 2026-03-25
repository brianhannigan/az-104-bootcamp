# AZ-104 Bootcamp – Day 6  
## Monitoring & Backup (HIGH VALUE – STRONG OVERLAP WITH SECURITY)

---

# 🔥 Why This Matters

This section is where YOU gain advantage.

You already have:
- Sentinel exposure ✅
- Threat hunting mindset ✅

AZ-104 tests:
- Monitoring setup
- Alert logic
- Log queries
- Backup strategies

👉 This is EASY points if done right

---

# 🧠 Day 6 Objectives

- Understand Azure Monitor (CORE)
- Learn Log Analytics (VERY TESTED)
- Create alerts and action groups
- Understand metrics vs logs
- Learn Azure Backup and Recovery Services Vault

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 📊 Azure Monitor (CORE SERVICE)

Azure Monitor = **central monitoring system**

Collects:
- Metrics
- Logs

---

## 🔥 Metrics vs Logs (VERY IMPORTANT)

| Feature | Metrics | Logs |
|--------|--------|------|
| Speed | Fast | Slower |
| Detail | Low | High |
| Use | Alerts | Analysis |

---

## 🧠 Simple Rule

Metrics = “Is something wrong?”  
Logs = “What exactly happened?”

---

## 📦 Log Analytics Workspace

Where logs are stored and queried

👉 Used with KQL

---

## 🔥 EXAM KEY

If question says:
“Query logs”

👉 Answer = Log Analytics

---

## 🔎 KQL (Query Language)

Used to:
- Search logs
- Investigate issues
- Build alerts

---

## 🧠 Example Tables

- Heartbeat (VM status)
- SecurityEvent
- AzureActivity
- DeviceProcessEvents (your background)

---

## 🚨 Alerts

Trigger when condition met

---

## 🔥 Types of Alerts

| Type | Use |
|------|-----|
| Metric Alert | CPU, memory |
| Log Alert | KQL query |

---

## 🧠 Action Groups

What happens when alert triggers:
- Email
- SMS
- Webhook

---

## 🔥 EXAM FLOW

Condition → Alert → Action Group → Notification

---

## 🔐 Azure Backup

Used to:
- Protect VMs
- Restore data

---

## 🧠 Recovery Services Vault

Storage for backups

---

## 🔥 EXAM KEY

Backup ALWAYS requires:
👉 Recovery Services Vault

---

## 🔁 Backup Types

- Full
- Incremental (most common)

---

## 🔥 Restore Options

- Full VM restore
- File-level restore

---

## ⏳ Retention

How long backups are kept

---

## 🔥 EXAM TRICK

Longer retention = higher cost

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Monitor VM
- Query logs
- Create alerts
- Configure backup

---

## 🔧 Portal Steps

### 1. Create Log Analytics Workspace

Name: law-day6

---

### 2. Connect VM

Enable:
- Monitoring agent
- Send logs to workspace

---

### 3. Run KQL Query

Example:

Heartbeat  
| take 10  

---

### 4. Create Alert

Condition:
- CPU > 80%

---

### 5. Create Action Group

- Email notification

---

### 6. Trigger Alert

Simulate CPU load

---

### 7. Create Recovery Services Vault

Name: rsv-day6

---

### 8. Enable Backup

- Select VM
- Configure policy

---

### 9. Run Backup

Perform initial backup

---

### 10. Test Restore

File-level restore

---

# 💻 CLI COMMANDS

Create workspace:

az monitor log-analytics workspace create \
  --resource-group rg-day1-core \
  --workspace-name law-day6

---

Create alert:

az monitor metrics alert create \
  --name cpu-alert \
  --resource-group rg-day1-core \
  --scopes <VM_ID> \
  --condition "avg Percentage CPU > 80"

---

# 💻 PowerShell COMMANDS

New-AzOperationalInsightsWorkspace `
  -ResourceGroupName rg-day1-core `
  -Name law-day6 `
  -Location EastUS

---

# 🔹 STEP 3 – EXAM TRAPS

❌ Trap 1  
Using Metrics when Logs needed  
👉 Logs = detailed analysis

---

❌ Trap 2  
Forgetting Log Analytics  
👉 Required for KQL

---

❌ Trap 3  
Alert without action group  
👉 No notification

---

❌ Trap 4  
Backup without vault  
👉 Not possible

---

❌ Trap 5  
Confusing Sentinel vs Monitor  
👉 Sentinel = SIEM  
👉 Monitor = core service

---

❌ Trap 6  
Retention ignored  
👉 Impacts cost

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

Q1  
Where are logs stored?

A. NSG  
B. Log Analytics  
C. VM  
D. Disk  

Answer: B

---

Q2  
Fast alert for CPU spike:

A. Log alert  
B. Metric alert  
C. NSG  
D. Policy  

Answer: B

---

Q3  
Query logs:

A. SQL  
B. PowerShell  
C. KQL  
D. Bash  

Answer: C

---

Q4  
Backup requires:

A. NSG  
B. Vault  
C. Tag  
D. Policy  

Answer: B

---

Q5  
Detailed investigation:

A. Metrics  
B. Logs  
C. NSG  
D. Disk  

Answer: B

---

Q6  
Send alert email:

A. Action Group  
B. Policy  
C. RBAC  
D. Tag  

Answer: A

---

Q7  
Retention affects:

A. Security  
B. Cost  
C. Network  
D. DNS  

Answer: B

---

# 🧠 MUST MEMORIZE

- Monitor = central  
- Logs = Log Analytics  
- Metrics = fast alerts  

- Alert → Action Group  

- Backup → Recovery Vault  

---

# 🔁 Reinforcement

Repeat:

- Metrics vs Logs
- Alert flow
- Backup components

---

# 🚨 Homework

1. Create workspace
2. Connect VM
3. Run KQL query
4. Create alert
5. Configure backup
6. Answer:

👉 When do you use metrics vs logs?  
👉 What component is REQUIRED for backup?

---

# ⏭️ Next: Day 7 (Governance & Cost Management)

- Azure Policy deep dive
- Cost management
- Resource organization strategies
