# AZ-104 Bootcamp – Day 5  
## Compute (VMs & App Services – HIGH IMPACT)

---

# 🔥 Why This Matters

Compute is a MAJOR portion of AZ-104.

Microsoft tests:
- VM deployment decisions
- Scaling behavior
- Availability design
- App Service vs VM scenarios

👉 Expect scenario-based questions.

---

# 🧠 Day 5 Objectives

- Deploy and manage VMs
- Understand VM sizing and disks
- Learn availability (VERY TESTED)
- Understand VM Scale Sets
- Learn App Services basics



## 📚 Microsoft Learn Links (Use with Each Section)

- Create a Windows virtual machine in Azure module: https://learn.microsoft.com/en-us/training/modules/create-windows-virtual-machine-in-azure/
- Configure and manage virtual networks for Azure administrators module: https://learn.microsoft.com/en-us/training/modules/configure-manage-virtual-networks-azure-admin/
- Host a web application with Azure App Service module: https://learn.microsoft.com/en-us/training/modules/host-a-web-app-with-azure-app-service/

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

## ⏲️ Day Timer

[▶ Open running timers for this day](../assets/running-timers.html?day=day05)

| Timer | Target |
|---|---|
| Total Day Timer | 8h 00m |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

**⏲️ Session Timer:** 2h 15m

## 🖥️ Virtual Machines (VMs)

VM = full control compute

You manage:
- OS
- Patching
- Security
- Networking

---

## 🔥 VM Components

| Component | Purpose |
|----------|--------|
| Size | CPU / RAM |
| OS Disk | Boot disk |
| Data Disk | Storage |
| NIC | Network |
| NSG | Security |

---

## 🧩 VM Extensions (ADVANCED)

- Custom Script Extension → run post-deployment scripts
- Azure Monitor Agent → send telemetry/logs

---

## 🧠 VM Sizing

Choose based on:
- CPU
- Memory
- Workload

👉 EXAM TIP: Right-size to save cost

---

## 💾 Disk Types

| Type | Use |
|------|-----|
| Standard HDD | Cheap, slow |
| Standard SSD | Balanced |
| Premium SSD | High performance |

---

## 🔐 Disk Encryption

- Azure Disk Encryption (ADE)
- Commonly integrates with Azure Key Vault for key management

---

## 🛠️ Run Command

Run commands in VM from Azure control plane without direct SSH/RDP session.

---

## 🔥 Availability (VERY TESTED)

### 1. Availability Set

Protects from:
- Hardware failure
- Maintenance

---

### 2. Availability Zones

- Different datacenters
- Higher resilience

---

## 🔥 EXAM RULE

| Requirement | Use |
|------------|-----|
| Same datacenter protection | Availability Set |
| Different datacenters | Availability Zones |

---

## 📈 VM Scale Sets (VMSS)

Auto-scale VMs

Used for:
- Web apps
- High traffic systems

---

## 🔥 EXAM KEY

Scaling automatically = VM Scale Set

---

## 🌐 App Services

PaaS (Platform as a Service)

You do NOT manage:
- OS
- Patching

---

## 🧠 When to Use App Service

- Web apps
- APIs
- Fast deployment

---

## 🔥 VM vs App Service

| Feature | VM | App Service |
|--------|---|------------|
| OS control | Yes | No |
| Maintenance | You | Azure |
| Scaling | Manual/VMSS | Built-in |

---

## 🔐 App Service Plans

Defines:
- Pricing
- Scaling
- Region

---

## 🔥 EXAM TRICK

Multiple apps can share ONE App Service Plan

---

# 🔹 STEP 2 – HANDS-ON LAB

**⏲️ Session Timer:** 3h 00m

## 🎯 Scenario

You will:
- Deploy VM
- Configure availability
- Scale environment
- Deploy App Service

---

## 🔧 Portal Steps

### 1. Create VM

Name: vm-day5  
Size: B2s (cheap)  
OS: Ubuntu or Windows  

---

### 2. Attach Disk

Add data disk

---

### 3. Configure NSG

Allow:
- SSH (22) or RDP (3389)

---

### 4. Create Availability Set

Add VM to set

---

### 5. (Optional Advanced)

Deploy VM in Availability Zone

---

### 6. Create VM Scale Set

Enable auto-scale

---

### 7. Create App Service

- Name: app-day5  
- Runtime: .NET / Node  

---

### 8. Deploy Sample App

Use default template

---

# 💻 CLI COMMANDS

Create VM:

az vm create \
  --name vm-day5 \
  --resource-group rg-day1-core \
  --image UbuntuLTS \
  --size Standard_B2s \
  --admin-username azureuser \
  --generate-ssh-keys

---

Create VMSS:

az vmss create \
  --name vmss-day5 \
  --resource-group rg-day1-core \
  --image UbuntuLTS \
  --instance-count 2 \
  --upgrade-policy-mode automatic

---

Create App Service:

az webapp up \
  --name app-day5 \
  --resource-group rg-day1-core

---

# 💻 PowerShell COMMANDS

New-AzVM `
  -ResourceGroupName rg-day1-core `
  -Name vm-day5 `
  -Location EastUS

---

# 🔹 STEP 3 – EXAM TRAPS

**⏲️ Session Timer:** 1h 00m

❌ Trap 1  
Using VM when App Service is better  
👉 Use App Service for web apps

---

❌ Trap 2  
Availability Set vs Zone confusion  
👉 Set = same DC  
👉 Zone = different DC

---

❌ Trap 3  
Scaling manually  
👉 Use VMSS for auto-scale

---

❌ Trap 4  
Thinking App Service needs OS patching  
👉 Azure handles it

---

❌ Trap 5  
Over-sizing VM  
👉 Cost optimization matters

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

**⏲️ Session Timer:** 1h 45m

Q1  
Need full OS control:

A. App Service  
B. VM  
C. Storage  
D. Function  

Answer: B

---

Q2  
Web app with minimal management:

A. VM  
B. App Service  
C. Disk  
D. NSG  

Answer: B

---

Q3  
High availability across datacenters:

A. Availability Set  
B. Availability Zone  
C. NSG  
D. Policy  

Answer: B

---

Q4  
Auto-scale compute:

A. VM  
B. NSG  
C. VMSS  
D. Disk  

Answer: C

---

Q5  
Multiple apps share compute:

A. VM  
B. Disk  
C. App Service Plan  
D. RBAC  

Answer: C

---

Q6  
Cheapest disk:

A. Premium SSD  
B. Standard SSD  
C. Standard HDD  
D. ZRS  

Answer: C

---

Q7  
Reduce downtime in same DC:

A. Zone  
B. Set  
C. Policy  
D. NSG  

Answer: B

---

# 🧠 MUST MEMORIZE

- VM = full control  
- App Service = managed  

- Availability Set vs Zone  

- VMSS = scaling  

- App Service Plan = shared compute  

---

# 🔁 Reinforcement

Repeat:

- VM vs App Service
- Set vs Zone
- VMSS purpose

---

# 🚨 Homework

1. Deploy VM
2. Add disk
3. Create App Service
4. Test both
5. Answer:

👉 When would you choose VM over App Service?  
👉 How do you scale automatically?

---

# ⏭️ Next: Day 6 (Monitoring & Backup)

- Azure Monitor
- Log Analytics
- Alerts
- Backup & Recovery
