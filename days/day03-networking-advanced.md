# AZ-104 Bootcamp – Day 3  
## Advanced Networking (HIGH IMPACT – SCENARIO HEAVY)

---

# 🔥 Why This Matters

Day 3 is where networking becomes **exam-level**.

Microsoft will test:
- “How do these networks connect?”
- “Why is traffic not flowing?”
- “What is the BEST solution?”

👉 This is NOT memorization — this is **understanding flow**

---

# 🧠 Day 3 Objectives

- Master VNet Peering (VERY TESTED)
- Understand routing (system vs custom routes)
- Learn UDR (User Defined Routes)
- Understand Private Endpoints
- Learn hybrid connectivity basics (VPN Gateway)

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 🔗 VNet Peering

VNet Peering connects two VNets **privately over Azure backbone**

👉 No internet involved

---

## 🧠 Key Properties

- Low latency
- High bandwidth
- Private IP communication
- Same or different regions

---

## 🔥 CRITICAL RULE

Peering is **NOT transitive**

Example:

VNet A ↔ VNet B  
VNet B ↔ VNet C  

👉 A CANNOT talk to C

---

## 🔁 Peering is Bidirectional

You must configure peering **on BOTH VNets**

---

## 🧠 Peering Options (Important)

| Setting | Meaning |
|--------|--------|
| Allow VNet Access | Enables communication |
| Allow Forwarded Traffic | Needed for appliances |
| Allow Gateway Transit | Use remote gateway |
| Use Remote Gateway | Use another VNet's gateway |

---

## 🛣️ Routing in Azure

Azure has **system routes by default**

Example:
- VNet → VNet traffic works automatically

---

## 🔥 When You Need UDR

Use UDR when:
- You want to control traffic path
- Force traffic through firewall/NVA
- Override default behavior

---

## 🧠 UDR (User Defined Route)

Custom route table:
- Destination
- Next hop

---

## 🧠 Example

Send all traffic to firewall:

0.0.0.0/0 → Firewall IP

---

## 🔥 EXAM TRICK

If question says:
“Force all traffic through inspection device”

👉 Answer = UDR

---

## 🔐 Private Endpoints

Private Endpoint = access Azure service via **private IP**

Example:
- Storage account accessed inside VNet

---

## 🧠 Why Use It?

- No public internet
- Secure access
- Internal communication

---

## 🔥 EXAM KEY

Private Endpoint vs Service Endpoint:

| Feature | Difference |
|--------|----------|
| Private Endpoint | Private IP |
| Service Endpoint | Public IP but restricted |

---

## 🔐 Azure Firewall vs NSG (EXAM COMPARISON)

| NSG | Azure Firewall |
|-----|----------------|
| Basic L3/L4 filtering | Advanced centralized filtering |
| Applied to subnet/NIC | Deployed as managed firewall service |
| No built-in NAT scenarios focus | Supports DNAT/SNAT scenarios |

🔥 Rule of thumb: NSG for segment-level filtering, Azure Firewall for centralized and advanced control.

---

## 🛡️ Azure Bastion

- Secure RDP/SSH through browser
- No public IP required on target VMs

👉 If exam asks for secure admin access without exposing VM public IP, Bastion is a top answer.

---

## ⚖️ Load Balancer vs Application Gateway

| Service | Layer | Best for |
|--------|-------|----------|
| Azure Load Balancer | Layer 4 | TCP/UDP distribution |
| Application Gateway | Layer 7 | HTTP/HTTPS routing + WAF scenarios |

---

## 🌉 Hybrid Connectivity Options

| Type | Use |
|------|-----|
| VPN Gateway | Encrypted tunnel over internet |
| ExpressRoute | Private dedicated connectivity |

---

## 🌉 VPN Gateway (Basic Understanding)

Used for:
- On-prem to Azure connection
- Site-to-site or point-to-site

---

## 🔥 KEY IDEA

- VPN = encrypted tunnel
- Used for hybrid environments

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Create 2 VNets
- Peer them
- Add route table
- Simulate traffic control

---

## 🔧 Portal Steps

### 1. Create VNet A

Name: vnet-a  
Address: 10.1.0.0/16  

Subnet:
10.1.1.0/24  

---

### 2. Create VNet B

Name: vnet-b  
Address: 10.2.0.0/16  

Subnet:
10.2.1.0/24  

---

### 3. Peer VNets

From vnet-a:
- Peer to vnet-b

From vnet-b:
- Peer to vnet-a

---

### 4. Enable Settings

- Allow VNet Access = YES

---

### 5. Deploy VM in each VNet

---

### 6. Test Connectivity

Ping or connect between VMs

👉 Should work

---

### 7. Create Route Table

Name: rt-custom

---

### 8. Add Route

Destination:
0.0.0.0/0  

Next Hop:
Virtual Appliance (fake or placeholder)

---

### 9. Associate Route Table

Attach to subnet

---

### 10. Observe Behavior

Traffic routing changes

---

# 💻 CLI COMMANDS

Create VNet A:

az network vnet create \
  --name vnet-a \
  --resource-group rg-day1-core \
  --address-prefix 10.1.0.0/16 \
  --subnet-name subnet-a \
  --subnet-prefix 10.1.1.0/24

---

Create VNet B:

az network vnet create \
  --name vnet-b \
  --resource-group rg-day1-core \
  --address-prefix 10.2.0.0/16 \
  --subnet-name subnet-b \
  --subnet-prefix 10.2.1.0/24

---

Create Peering:

az network vnet peering create \
  --name peer-a-to-b \
  --resource-group rg-day1-core \
  --vnet-name vnet-a \
  --remote-vnet vnet-b \
  --allow-vnet-access

---

Create Route Table:

az network route-table create \
  --name rt-custom \
  --resource-group rg-day1-core

---

# 💻 PowerShell COMMANDS

New-AzVirtualNetwork `
  -Name vnet-a `
  -ResourceGroupName rg-day1-core `
  -Location EastUS `
  -AddressPrefix 10.1.0.0/16

---

New-AzRouteTable `
  -Name rt-custom `
  -ResourceGroupName rg-day1-core `
  -Location EastUS

---

# 🔹 STEP 3 – EXAM TRAPS

❌ Trap 1  
Peering assumed transitive  
👉 It is NOT

---

❌ Trap 2  
Forcing traffic through firewall  
👉 Must use UDR

---

❌ Trap 3  
Private endpoint vs service endpoint confusion  
👉 Private endpoint = private IP

---

❌ Trap 4  
Peering only configured one way  
👉 Must be bidirectional

---

❌ Trap 5  
Routing ignored  
👉 System routes exist unless overridden

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

Q1  
Peering allows:

A. Internet traffic  
B. Private VNet communication  
C. Storage access  
D. DNS only  

Answer: B

---

Q2  
Peering is:

A. Transitive  
B. One-way  
C. Bidirectional  
D. Public  

Answer: C

---

Q3  
Force traffic through firewall:

A. NSG  
B. UDR  
C. Tag  
D. Policy  

Answer: B

---

Q4  
Private Endpoint provides:

A. Public access  
B. Private IP access  
C. DNS only  
D. Load balancing  

Answer: B

---

Q5  
Two VNets connected through B cannot communicate A→C. Why?

A. NSG  
B. DNS  
C. Peering not transitive  
D. Policy  

Answer: C

---

Q6  
Route tables control:

A. Identity  
B. Traffic path  
C. Storage  
D. Compute  

Answer: B

---

Q7  
VPN Gateway is used for:

A. VM scaling  
B. Hybrid connectivity  
C. Storage  
D. NSG  

Answer: B

---

# 🧠 MUST MEMORIZE

- Peering = private connection  
- NOT transitive  
- Must configure both sides  

- UDR = custom routing  
- Private Endpoint = private IP access  

---

# 🔁 Reinforcement

Repeat:

- Peering rules
- Routing behavior
- UDR vs NSG
- Private vs Service Endpoint

---

# 🚨 Homework

1. Build both VNets
2. Peer them
3. Break connectivity (remove peering)
4. Add route table
5. Answer:

👉 Why did traffic stop?  
👉 What fixed it?

---

# ⏭️ Next: Day 4 (Storage – HIGHLY TESTED)

- Blob vs File vs Disk
- Redundancy
- Lifecycle rules
- Data protection
