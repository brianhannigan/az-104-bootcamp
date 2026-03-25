# AZ-104 Bootcamp – Day 2  
## Networking Core (CRITICAL – MOST TESTED AREA)

---

# 🔥 Why This Matters

Networking is where most people FAIL AZ-104.

It shows up in:
- VM questions
- Storage access
- App Services
- Security scenarios

👉 If you master networking, you pass faster.

---

# 🧠 Day 2 Objectives

- Understand VNets and subnets deeply
- Learn NSG behavior (VERY IMPORTANT)
- Understand IP addressing (public vs private)
- Learn Azure DNS basics
- Control traffic flow and troubleshoot connectivity



## 📚 Microsoft Learn Links (Use with Each Section)

- Azure networking services overview: https://learn.microsoft.com/en-us/azure/networking/fundamentals/networking-overview
- Introduction to Azure virtual networks module: https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-virtual-networks/
- Introduction to network security groups module: https://learn.microsoft.com/en-us/training/modules/intro-to-azure-network-security-groups/

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

## ⏲️ Day Timer

[▶ Open running timers for this day](../assets/running-timers.html?day=day02)

| Timer | Target |
|---|---|
| Total Day Timer | 8h 00m |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

**⏲️ Session Timer:** 2h 15m

## 🧩 Core Networking Model

Internet  
↓  
Public IP  
↓  
Subnet  
↓  
VM  

---

## 🌐 Virtual Network (VNet)

Think of a VNet like your **company network in the cloud**.

- Private network space
- Fully isolated by default
- Uses IP ranges (CIDR)

Example:
10.0.0.0/16

---

## 🔀 Subnets

Subnets divide your VNet.

Example:

VNet: 10.0.0.0/16  
- Subnet1: 10.0.1.0/24  
- Subnet2: 10.0.2.0/24  

👉 Used for:
- Isolation
- Security boundaries
- Applying NSGs

---

## 🔑 CRITICAL RULE

You deploy resources into **subnets**, NOT VNets directly.

---

## 🌍 Public vs Private IP

| Type | Purpose |
|------|--------|
| Public IP | Internet access |
| Private IP | Internal communication |

---

## 🔐 Network Security Groups (NSG)

NSG = **Firewall for Azure resources**

Controls:
- Inbound traffic
- Outbound traffic

---

## 🔥 NSG RULE PROCESSING (HIGHLY TESTED)

- Rules processed by **priority**
- Lower number = higher priority
- First match wins

---

## 🧠 NSG Example

Allow SSH:
Priority: 100  
Allow TCP 22  

Deny All:
Priority: 4096  

👉 SSH allowed because 100 < 4096

---

## 🔑 NSG Scope

NSGs can be applied to:
- Subnet
- Network Interface (NIC)

---

## 🔥 EXAM TRICK

If both NSG exist:

👉 BOTH must allow traffic

---

## 🌐 DNS (Simple Version)

Azure provides:
- Default DNS (automatic)
- Custom DNS (you configure)

---

## 🧠 Name Resolution

VMs can talk using:
- IP address
- Hostname (via DNS)

---

## 🔥 KEY RULE

If DNS is wrong → connectivity fails even if network is fine

---

# 🔹 STEP 2 – HANDS-ON LAB

**⏲️ Session Timer:** 3h 15m

## 🎯 Scenario

You will:
- Build a network
- Deploy a VM
- Control traffic with NSG
- Break and fix connectivity

---

## 🔧 Portal Steps

### 1. Create VNet

Name: vnet-day2  
Address space: 10.0.0.0/16  

---

### 2. Create Subnets

Subnet1:
- Name: frontend
- 10.0.1.0/24  

Subnet2:
- Name: backend
- 10.0.2.0/24  

---

### 3. Deploy VM

- Place in frontend subnet
- Enable public IP

---

### 4. Create NSG

Name: nsg-frontend

---

### 5. Add Rule

Allow:
- Port 22 (Linux) OR 3389 (Windows)
- Priority: 100

---

### 6. Associate NSG

Attach to:
👉 frontend subnet

---

### 7. Test Connectivity

- Connect via SSH/RDP
- Confirm access works

---

### 8. BREAK IT (IMPORTANT)

Add rule:
- Deny all inbound
- Priority: 50

👉 Now connection should FAIL

---

### 9. FIX IT

Remove deny OR change priority

---

# 💻 CLI COMMANDS

Create VNet:

az network vnet create \
  --name vnet-day2 \
  --resource-group rg-day1-core \
  --address-prefix 10.0.0.0/16 \
  --subnet-name frontend \
  --subnet-prefix 10.0.1.0/24

---

Create NSG:

az network nsg create \
  --name nsg-frontend \
  --resource-group rg-day1-core

---

Add rule:

az network nsg rule create \
  --nsg-name nsg-frontend \
  --resource-group rg-day1-core \
  --name allow-ssh \
  --priority 100 \
  --access Allow \
  --protocol Tcp \
  --destination-port-range 22

---

# 💻 PowerShell COMMANDS

New-AzVirtualNetwork `
  -Name vnet-day2 `
  -ResourceGroupName rg-day1-core `
  -Location EastUS `
  -AddressPrefix 10.0.0.0/16

---

New-AzNetworkSecurityGroup `
  -Name nsg-frontend `
  -ResourceGroupName rg-day1-core `
  -Location EastUS

---

# 🔹 STEP 3 – EXAM TRAPS

**⏲️ Session Timer:** 45m

❌ Trap 1  
NSG rule priority misunderstood  
👉 Lower number = higher priority

---

❌ Trap 2  
NSG vs Firewall  
👉 NSG = basic filtering  
👉 Firewall = advanced

---

❌ Trap 3  
Subnet vs VNet confusion  
👉 NSG applied at subnet affects ALL resources

---

❌ Trap 4  
Connectivity issue  
👉 Could be DNS, not NSG

---

❌ Trap 5  
Traffic allowed on NIC but blocked on subnet  
👉 BOTH must allow

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

**⏲️ Session Timer:** 1h 45m

Q1  
What does an NSG control?

A. Identity  
B. Storage  
C. Network traffic  
D. Cost  

Answer: C

---

Q2  
Which rule is applied first?

A. Highest number  
B. Lowest number  
C. Random  
D. Last created  

Answer: B

---

Q3  
You cannot connect to VM. NSG allows port. Why?

A. DNS issue  
B. Disk issue  
C. RBAC issue  
D. Tag missing  

Answer: A

---

Q4  
Where can NSG be applied?

A. Subscription  
B. Resource Group  
C. Subnet or NIC  
D. Storage account  

Answer: C

---

Q5  
Which IP allows internet access?

A. Private IP  
B. Public IP  
C. Subnet  
D. DNS  

Answer: B

---

Q6  
You must isolate traffic between tiers. Use?

A. Tags  
B. Subnets  
C. Locks  
D. Policy  

Answer: B

---

Q7  
Two NSGs applied (Subnet + NIC). Traffic allowed only if?

A. Either allows  
B. Both allow  
C. One denies  
D. DNS allows  

Answer: B

---

# 🧠 MUST MEMORIZE

- VNet = network  
- Subnet = segmentation  
- NSG = firewall  
- Public IP = internet  
- Private IP = internal  

- NSG rules:
  Lower number = higher priority  
  First match wins  

---

# 🔁 Reinforcement

Repeat without looking:

- NSG rule processing
- Subnet vs VNet
- Public vs Private IP
- Where NSGs apply

---

# 🚨 Homework

1. Build full lab
2. Break connectivity intentionally
3. Fix it
4. Answer:

👉 Why did it break?  
👉 Which rule caused it?

---

# ⏭️ Next: Day 3 (Advanced Networking)

- VNet Peering
- Route Tables (UDR)
- Private Endpoints
- Hybrid connectivity
