# AZ-104 Bootcamp – Day 4  
## Storage (HIGHLY TESTED – MANY TRICK QUESTIONS)

---

# 🔥 Why This Matters

Storage questions are everywhere on AZ-104.

Microsoft tests:
- “Which storage type should you use?”
- “How do you secure it?”
- “How do you reduce cost?”

👉 Most mistakes happen from mixing up storage types.

---

# 🧠 Day 4 Objectives

- Understand ALL storage types (Blob, File, Disk)
- Learn redundancy options (VERY TESTED)
- Secure storage (RBAC vs SAS vs Keys)
- Understand lifecycle management
- Learn access tiers (Hot, Cool, Archive)

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 🧩 Storage Account (CORE CONCEPT)

Everything starts with a **Storage Account**

Think of it like a **container for all storage services**

---

## 📦 Storage Types

### 1. Blob Storage (OBJECT STORAGE)

Used for:
- Images
- Videos
- Backups
- Logs

👉 MOST USED in exam questions

---

### 2. File Storage (AZURE FILES)

Used for:
- Shared file systems
- SMB access
- Lift-and-shift apps

---

### 3. Disk Storage

Used for:
- VM disks (OS + Data)

---

## 🔥 EXAM TIP

| Scenario | Use |
|---------|----|
| Store files for web/app | Blob |
| Shared drive | File |
| VM storage | Disk |

---

## 🧠 Redundancy (VERY IMPORTANT)

Defines how data is replicated

| Type | Meaning |
|------|--------|
| LRS | Local (single datacenter) |
| ZRS | Across zones |
| GRS | Secondary region |
| RA-GRS | Read access to secondary |

---

## 🔥 EXAM TRICK

- Need HIGH availability → ZRS or GRS  
- Need READ access secondary → RA-GRS  

---

## 🧊 Access Tiers

| Tier | Use |
|------|-----|
| Hot | Frequent access |
| Cool | Less frequent |
| Archive | Rare access |

---

## 🔥 COST RULE

Cheaper storage = slower access

---

## 🔐 Storage Security (VERY TESTED)

### 1. RBAC
- Best practice
- Azure AD based

---

### 2. SAS (Shared Access Signature)

Temporary access

Example:
- Give link for 1 hour

---

### 3. Access Keys

- Full access
- Least secure
- Avoid if possible

---

## 🔥 EXAM PRIORITY

RBAC > SAS > Keys

---

## 🌐 Network Security for Storage (HIGH VALUE)

| Feature | Purpose |
|--------|---------|
| Firewall | Restrict access by IP/network |
| Service Endpoint | Secure access from selected subnets |
| Private Endpoint | Private IP access from VNet |

🔥 Exam pattern: “internal-only/private access” → Private Endpoint.

---

## 🛡️ Data Protection Features

- Soft Delete → recover deleted blobs/files
- Versioning → restore previous object versions
- Immutability → prevent modification/deletion for retention window

---

## 🌐 Networking for Storage

You can:
- Allow public access
- Restrict by IP
- Use private endpoint

---

## 🔥 IMPORTANT

“Secure storage access internally”

👉 Answer = Private Endpoint

---

## 🔁 Lifecycle Management

Automatically move/delete data

Example:
- Move to Cool after 30 days
- Archive after 90 days

---

## 🔥 EXAM TRICK

Cost optimization = lifecycle policies

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Create storage account
- Upload data
- Secure access
- Configure lifecycle
- Test tiers

---

## 🔧 Portal Steps

### 1. Create Storage Account

Name: stday4storage  
Type: General Purpose v2  
Redundancy: LRS  

---

### 2. Create Container

Name: data

---

### 3. Upload File

Upload any file

---

### 4. Change Access Tier

Set:
- Hot → Cool → Archive

---

### 5. Configure Lifecycle Rule

Rule:
- Move to Cool after 30 days
- Archive after 90 days

---

### 6. Generate SAS

- Create read-only SAS
- Set expiration (1 hour)

---

### 7. Disable Public Access

- Turn OFF public access

---

### 8. (Optional Advanced)

Create Private Endpoint

---

# 💻 CLI COMMANDS

Create storage:

az storage account create \
  --name stday4storage \
  --resource-group rg-day1-core \
  --location eastus \
  --sku Standard_LRS

---

Create container:

az storage container create \
  --name data \
  --account-name stday4storage

---

Upload file:

az storage blob upload \
  --account-name stday4storage \
  --container-name data \
  --name test.txt \
  --file ./test.txt

---

# 💻 PowerShell COMMANDS

New-AzStorageAccount `
  -ResourceGroupName rg-day1-core `
  -Name stday4storage `
  -Location EastUS `
  -SkuName Standard_LRS

---

# 🔹 STEP 3 – EXAM TRAPS

❌ Trap 1  
Using Access Keys when RBAC is better  
👉 Always choose RBAC first

---

❌ Trap 2  
Confusing Blob vs File  
👉 Blob = object storage  
👉 File = shared drive

---

❌ Trap 3  
Wrong redundancy choice  
👉 GRS for DR  
👉 ZRS for availability

---

❌ Trap 4  
Cost optimization ignored  
👉 Lifecycle policies required

---

❌ Trap 5  
Public access left ON  
👉 Security risk

---

❌ Trap 6  
Private Endpoint vs Firewall  
👉 Private Endpoint = internal private IP

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

Q1  
Best storage for images?

A. File  
B. Disk  
C. Blob  
D. Queue  

Answer: C

---

Q2  
Need shared drive for multiple VMs:

A. Blob  
B. File  
C. Disk  
D. Archive  

Answer: B

---

Q3  
Need DR in another region:

A. LRS  
B. ZRS  
C. GRS  
D. Hot  

Answer: C

---

Q4  
Temporary access to file:

A. RBAC  
B. SAS  
C. Key  
D. Policy  

Answer: B

---

Q5  
Most secure access method:

A. Key  
B. SAS  
C. RBAC  
D. Public  

Answer: C

---

Q6  
Reduce cost automatically:

A. NSG  
B. Policy  
C. Lifecycle  
D. DNS  

Answer: C

---

Q7  
Private access to storage:

A. Public endpoint  
B. NSG  
C. Private Endpoint  
D. Tag  

Answer: C

---

# 🧠 MUST MEMORIZE

- Blob = object  
- File = shared  
- Disk = VM  

- LRS = local  
- ZRS = zones  
- GRS = region  

- RBAC > SAS > Keys  

- Hot / Cool / Archive  

---

# 🔁 Reinforcement

Repeat:

- Storage types
- Redundancy differences
- Access methods
- Tier usage

---

# 🚨 Homework

1. Build storage account
2. Upload files
3. Create SAS link
4. Disable public access
5. Answer:

👉 Which method was most secure?  
👉 How would you reduce cost over time?

---

# ⏭️ Next: Day 5 (Compute – VMs & App Services)

- VM deployment
- Scaling
- Availability Sets vs Zones
- App Services basics
