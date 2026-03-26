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

## 🏗️ What Happens When You Create a VM?

Creating an Azure VM is more than launching one server. Azure provisions and manages a **bundle of dependent resources**, such as:

- Compute host capacity
- OS/data disk storage
- Networking attachments
- Monitoring and diagnostics hooks
- Platform maintenance plumbing

👉 You focus on VM configuration and workload operations, while Azure handles physical infrastructure lifecycle and platform reliability.

---

## 💰 Understanding Azure VM Billing (HIGH-YIELD)

### Compute Costs
- **Compute charges start when a VM is running**
- Compute charges stop only when the VM is **deallocated**
  - Stopping from Azure Portal usually deallocates
  - Shutting down from inside the guest OS may not deallocate

### Ongoing Costs (Even When Deallocated)
These can still be billed:
- Managed disks
- Snapshots
- Public IP addresses (in certain SKU/allocation situations)

✅ **Key takeaway:** Stopping compute does **not** always mean zero cost.

---

## 🧠 Think Like an Azure Administrator

Every VM deployment should be intentional. These decisions directly affect cost, security, and performance:

- **Region** → latency, availability, compliance
- **VM size** → CPU, memory, cost
- **OS/image choice** → Linux/Windows, marketplace/custom image
- **Authentication** → password vs SSH keys
- **Networking model** → private vs internet-facing access
- **Disk tier** → IOPS, throughput, latency, price

👉 Overprovisioned or idle resources increase cost quickly. Right-size and review usage often.

---

## 🧱 VM as a Bundle of Connected Resources

A VM is not a standalone object; it depends on multiple connected services:

- NIC
- VNet + subnet
- NSG
- Optional public IP
- OS disk + data disks
- Monitoring/diagnostic settings

If one of these is missing or misconfigured, deployment can fail or the VM can be unreachable/insecure.

---

## 🌐 Networking Considerations

### Public IP Is Not the Default Safe Choice
- A public IP exposes the VM directly to the internet
- Use it only when there is a clear requirement

✅ **Best practices**
- Prefer private IP + Azure Bastion for administrative access
- Restrict NSG inbound rules to specific source IP ranges
- Keep only required ports open (22/3389 only when needed)
- Consider JIT VM access in Microsoft Defender for Cloud

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
| Ultra Disk | Extreme performance for specialized workloads |

### 🧠 Choosing the Right Disk Tier

Imagine you deploy a VM for a production database. At first, performance is fine. As traffic grows, disk throughput and latency can become the bottleneck. Requests queue up, and application responsiveness drops.

👉 Disk selection is a major architecture decision. You must balance:
- Performance (IOPS/throughput/latency)
- Cost
- Reliability requirements

**Quick guidance:**
- **Standard HDD** → development/testing, infrequent access, lowest cost
- **Standard SSD** → general-purpose/default choice, good price/performance
- **Premium SSD** → production databases and latency-sensitive workloads
- **Ultra Disk** → very demanding workloads requiring extremely high throughput and consistently low latency

### ✅ Scenario Mapping

- Small development server or test app → **Standard HDD**
- Moderate-traffic web app (for example, listings + inquiry form workflows) → **Standard SSD**
- Mission-critical database, analytics platform, or heavy social platform workload → **Premium SSD** or **Ultra Disk**

---

## Managing VM Disks and Disk Encryption

Azure managed disks are critical for both VM performance and cost management.

### Core Disk Concepts

- Every VM gets an **OS disk** by default (commonly around **127 GiB**, but image defaults can vary).
- You can attach **data disks** for databases, logs, backups, and application data.
- You can mix disk types in one VM (for example: Premium SSD for database files + Standard SSD for logs/backups).
- VM SKU limits still apply for:
  - Supported disk types
  - Max throughput and IOPS
  - Maximum number of attached disks (many VM sizes support up to 64 data disks)

### Temporary Disk (Important)

- Many VM sizes include temporary local storage with very fast I/O.
- Temporary disk data is **not persistent** and can be lost on reboot, stop/deallocate, host servicing, or redeployment.
- Use only for cache/scratch/ephemeral files, never for critical data.

### Attaching and Initializing Data Disks

From the Azure portal:
1. Open the VM and go to **Disks**.
2. Select **Add data disk**.
3. Choose an existing managed disk or create a new one.
4. Set disk name, type, and size.

Inside the guest OS:
- **Windows:** initialize and format in Disk Management, then assign a drive letter.
- **Linux:** use tools such as `lsblk`, create filesystem if needed, then mount.

### Encryption Options

- **Server-Side Encryption (SSE):** enabled by default on all managed disks using Microsoft-managed keys.
- **Customer-Managed Keys (CMK):** store keys in Azure Key Vault for additional governance (rotation, auditing, and revocation control).
- **Double encryption:** available for stricter compliance scenarios using both platform and customer key layers.
- **Azure Disk Encryption (ADE):** OS-level encryption (BitLocker on Windows / dm-crypt on Linux). Useful legacy knowledge, but planned retirement is **September 2028**, so migration planning is important.

---

## 📝 Exam Tips (Disk-Focused)

- Every VM has an OS disk; put databases/logs/app data on separate data disks when possible.
- Disk performance is constrained by both disk tier **and** VM size/SKU limits.
- Some high-performance VM SKUs require Premium SSD (or higher-compatible) OS disks.
- Temporary disks are never for persistent/critical data.
- SSE is default baseline encryption; use CMK when governance/compliance requires key ownership and tighter controls.
- ADE is older OS-level encryption and should be recognized as legacy compared with modern SSE + CMK patterns.

---

## 📚 Additional Resources

- Introduction to Azure managed disks: https://learn.microsoft.com/en-us/azure/virtual-machines/managed-disks-overview
- Azure managed disk types: https://learn.microsoft.com/en-us/azure/virtual-machines/disks-types
- Understand Azure Disk Storage billing: https://learn.microsoft.com/en-us/azure/virtual-machines/disks-understand-billing
- Overview of managed disk encryption options: https://learn.microsoft.com/en-us/azure/virtual-machines/disk-encryption-overview

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

### 🎬 Demo: Create and Configure a Virtual Machine

For this demonstration, start from a **completely blank state** inside a resource group:

1. In the resource group, select **Create**.
2. Search for **Virtual machine**, then select **Create** again.
3. In the configuration screen, focus on the core settings first (then review advanced options for exam prep):
   - **VM name**
   - **Region**
   - **Availability options** (for this demo: **No infrastructure redundancy required**)
   - **Image** (example: **Windows Server** image from Azure Marketplace)
   - **Size** (remember: size affects both performance and price)
   - **Administrator username/password**
4. Select **Next: Disks**:
   - Configure disk size and disk type.
   - Compare cost/performance tiers (for example, Premium SSD vs Standard SSD).
   - Add a data disk using **Create and attach a new disk** (example: 1 TB Premium SSD).
5. Select **Next: Networking**:
   - In a blank environment, create a new **VNet** and **subnet**.
   - Keep defaults where appropriate.
   - Create a new **Public IP** using **Create new** and assign a name.
6. Select **Review + create**, then **Create**.
7. Wait for deployment to complete (provisioning time varies by selected configuration).
8. Select **Go to resource**.
9. Confirm VM is in **Running** state and note the public IP address.
10. Test connectivity:
    - Select **Connect** and choose the first connection option.
    - From a Windows machine, use **RDP**.
    - Select **Download RDP file**, launch it, approve prompts, and sign in with your admin password.

✅ This gives you the baseline portal workflow for VM deployment and first access.

### 🧠 Demo Key Takeaways

- VM creation is a sequence of foundational decisions, starting with naming, region, image, and size.
- VM size and disk type have major impact on performance and monthly cost.
- Disk planning includes both OS disk and optional data disks.
- Networking dependencies (VNet, subnet, public IP, NSG behavior) are critical to successful access.
- Provisioning time should always be considered when planning operations.
- After deployment, validate runtime state and access path immediately (for Windows: RDP).

For stronger exam and real-world readiness, practice the same deployment via both the **Azure portal** and **CLI/PowerShell**, and explore advanced settings beyond the minimum flow.

---

### 🎬 Demo: Configure Azure Disk Encryption

For this new demonstration, we start from the previous one with our newly created and operational virtual machine, and we configure **Azure Disk Encryption (ADE)** to enable **BitLocker** disk encryption.

1. In the VM left menu, go to **Settings > Disks**.
2. Review available disks:
   - The **system disk**
   - The **data disk** added earlier
3. In the **Encryption** column, note that encryption is already enabled by default.
   - This is **Server-Side Encryption (SSE)** managed by Microsoft.
   - It is different from **Azure Disk Encryption (ADE)**, which is not enabled by default and uses BitLocker at the OS layer.
4. Select **Additional settings**.
5. In **Encryption settings**, choose to encrypt **all OS and data disks**.
6. Scroll down and create a **Key Vault** to store the BitLocker key:
   - Select **Create new**
   - Enter a Key Vault name
   - Select **Next**
7. In **Access configuration**, enable Azure Disk Encryption for volume encryption so the vault can be used by Microsoft services for ADE.
8. Select **Review + create**, then **Create**.
9. Return to ADE settings and create a key:
   - Select **Create new**
   - Provide a key name
   - Select key size (for compatibility, use **4096-bit / 4K**)
   - Select **Create**
10. Select **Save**.
11. Once completed, select **Go to resource**.
12. Confirm in the top-right notifications that the VM extension provisioning state is **Succeeded**.

To validate inside the VM:

1. Reconnect to the VM using **RDP**.
2. Open **PowerShell**.
3. Run:
   - `manage-bde -status C:`
4. Confirm:
   - **Percentage Encrypted: 100%**
   - **Protection Status: Protection On**

✅ This confirms Azure Disk Encryption has been successfully enabled on the virtual machine.

### 🧠 Demo Key Takeaways

Azure Disk Encryption (ADE) adds an additional protection layer on top of default Server-Side Encryption (SSE). While SSE is automatically enabled and uses Microsoft-managed keys, ADE enables OS-level encryption with BitLocker (Windows), helping satisfy stricter compliance and security requirements.

- Start by checking current disk encryption state in VM disk settings.
- Understand the distinction between **SSE (platform/storage layer)** and **ADE (guest OS layer)**.
- Enable ADE from VM disk settings and choose to encrypt OS and data disks.
- Use Azure Key Vault to store/manage encryption keys and configure required access.
- Monitor deployment through VM extension provisioning status.
- Validate encryption from inside the VM with `manage-bde -status`.

The key objective is understanding both the **why** (compliance/security control) and the **how** (configuration + validation workflow) for Azure Disk Encryption.

---

## 🧪 Exercise: Deploy and Manage a Secure VM

### Lesson

### Downloads

### Cloud Resources

### Introduction

Virtual Machines are one of the most common compute resources in Azure. However, if not deployed securely, they can become easy targets for attacks. In this exercise, you will learn how to deploy a Virtual Machine (VM) with secure access and proper configuration to ensure compliance and protection.

### Learning Objectives

By the end of this exercise, you will be able to:

- Deploy a VM using Azure Portal.
- Configure secure access with SSH keys.
- Apply a Network Security Group (NSG) to restrict traffic.

### Instructions

1. Open the Azure portal and navigate to **Virtual Machines**.
2. Select **Create** to create a new Virtual machine using the following details:

#### Basics tab

- Select an existing **Resource group** (or create a new one).
- Give your new VM a **Virtual machine name**.
- Choose the **Region** closest to you.
- For **Availability options**, select **No infrastructure redundancy required**.
- For **Security type**, select **Trusted launch virtual machines**.
- Select **Ubuntu Server 24.04 LTS - x64 Gen2** as the image for the VM operating system. The available choices will change depending on the Security Type selected.
- For **Size**, click **See all sizes** and select **Standard_B1s - 1 vcpu, 1 GiB memory**.
- For **SSH public key source**, select **Generate new key pair**. Azure will create a new RSA key and prompt you to download the private key for later access. Save it in a secure location to use during SSH login.
- Select **RSA SSH Format** as SSH Key Type.
- Give a name for the SSH public key for the **Key pair name**. You may leave it as the default.
- For **Public inbound ports**, select **None**. Do **NOT** keep the default selection of **Allow selected ports**.

#### Networking tab

- Create a new Virtual network using the default values for it and the Subnet.
- Set **Public IP** to **None**. This will not expose the machine to the internet.
- Select **Delete NIC when the VM is deleted**.

#### Management tab

- Under **Identity**, select **Enable system-assigned managed identity**.

3. Select **Review + create**, then **Create** to create the VM.
4. When prompted, select **Download private key and create resource**.

### Availability

#### Question 1 of 3

When deploying a secure Virtual Machine in Azure, we chose not to assign a public IP address. Why is this considered a best practice?

#### Question 2 of 3

Match each Azure VM Security Type with its correct description.

These are the correct matches.

| Security Type | Description |
|---|---|
| Standard | Basic security features without additional hardware-based protections. |
| Trusted launch virtual machines | Provides advanced hardware-based security features such as Secure Boot and virtual TPM to protect against rootkits and bootkits. |
| Confidential virtual machines | Protects sensitive data in memory with encryption, ensuring that even Azure administrator cannot access it. |

#### Question 3 of 3

You deployed a Virtual Machine in Azure without a public IP address. Which of the following are valid ways to securely log into the VM? Select all that apply.

---

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
