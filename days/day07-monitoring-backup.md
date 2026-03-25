# AZ-104 Bootcamp – Day 7  
## Monitoring & Backup (HIGH VALUE – STRONG OVERLAP WITH SECURITY)

---

# 🔥 Why This Matters

This section is where you gain easy exam points.

AZ-104 tests:
- Monitoring setup and alerting
- Logs vs metrics decisions
- Diagnostic settings
- Backup and disaster recovery strategy

---

# 🧠 Day 7 Objectives

- Understand Azure Monitor (CORE)
- Learn Log Analytics and KQL
- Configure diagnostic settings correctly
- Understand Azure Backup + Recovery Services Vault
- Learn Azure Site Recovery (ASR), RPO, and RTO

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 📊 Azure Monitor

Azure Monitor collects and analyzes:
- Metrics
- Logs

---

## 🔥 Metrics vs Logs (VERY IMPORTANT)

| Feature | Metrics | Logs |
|--------|--------|------|
| Speed | Fast | Slower |
| Detail | Lower | Higher |
| Typical use | Near real-time alerting | Deep investigation |

---

## 🧾 Log Types (ADVANCED)

| Type | Description |
|------|------------|
| Activity Log | Subscription-level operations |
| Resource Logs | Resource-level diagnostic events |

---

## 📦 Log Analytics Workspace

Where logs are stored and queried with KQL.

🔥 Exam key: “run query across logs” → Log Analytics Workspace.

---

## 🔎 KQL Example

```kql
DeviceProcessEvents
| where ProcessCommandLine contains "powershell"
```

---

## ⚙️ Diagnostic Settings (HIGHLY TESTED)

Diagnostic settings are required to send platform/resource logs to:
- Log Analytics
- Storage account
- Event Hub

👉 Without diagnostic settings, key logs may never arrive.

---

## 🚨 Alerts + Action Groups

Alert flow:
Condition → Alert rule → Action Group → Notification/Automation

| Alert Type | Use |
|-----------|-----|
| Metric alert | CPU/memory thresholds |
| Log alert | KQL-based conditions |

---

## 🔐 Azure Backup

- Protects VMs/files/workloads
- Uses Recovery Services Vault

🔥 Exam key: backup for Azure VMs generally uses a Recovery Services Vault.

---

## ♻️ Azure Site Recovery (ASR)

Used for disaster recovery/failover of full workloads (commonly VMs).

---

## 🧠 DR Concepts

| Term | Meaning |
|------|--------|
| RPO | Acceptable data loss |
| RTO | Acceptable downtime |

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Enable monitoring for a VM
- Send logs to Log Analytics
- Create alerts and action groups
- Configure backup
- Review DR/failover options

---

## 🔧 Portal Steps

### 1. Create Log Analytics Workspace
Name: law-day7

---

### 2. Configure Diagnostic Settings
Send logs for target resources to the workspace

---

### 3. Run KQL Query
```kql
Heartbeat
| take 10
```

---

### 4. Create Alert Rule
Trigger on CPU threshold or query condition

---

### 5. Create Recovery Services Vault
Name: rsv-day7

---

### 6. Enable Backup for VM
Set policy and retention

---

### 7. Review ASR Setup (Optional Advanced)
Identify source/target region and failover workflow
