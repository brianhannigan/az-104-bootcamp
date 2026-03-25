# AZ-104 Bootcamp – Day 6  
## App Services & Containers (PaaS FOCUS – HIGH VALUE)

---

# 🔥 Why This Matters

This day bridges compute + modern app hosting.

AZ-104 tests:
- App Service configuration
- Deployment slots
- Authentication + networking for apps
- Container hosting options in Azure

👉 This is commonly mixed into scenario questions with networking and monitoring.

---

# 🧠 Day 6 Objectives

- Deepen App Service knowledge
- Understand App Service Plan behavior
- Learn deployment slots and swap strategy
- Learn container options (ACI / AKS awareness / Web App for Containers)
- Connect app hosting decisions to exam scenarios



## 📚 Microsoft Learn Links (Use with Each Section)

- Explore Azure App Service module: https://learn.microsoft.com/en-us/training/modules/introduction-to-azure-app-service/
- Deploy a website to Azure with Azure App Service module: https://learn.microsoft.com/en-us/training/modules/deploy-run-container-app-service/
- Run containerized applications in Azure Container Instances module: https://learn.microsoft.com/en-us/training/modules/run-docker-with-azure-container-instances/

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 🌐 Azure App Service (Core PaaS)

Best for:
- Web apps
- APIs
- Rapid deployments

You manage:
- App code
- App settings

Azure manages:
- OS patching
- Runtime platform
- Underlying infrastructure

---

## 🧠 App Service Plan (VERY TESTED)

Plan defines:
- Region
- Pricing tier
- Scale (instance size/count)

🔥 Key rule: multiple web apps can share one App Service Plan.

---

## 🔁 Deployment Slots

Use slots (dev/stage/prod) to:
- Validate before production
- Swap with minimal downtime

🔥 Exam pattern: “test new version before production cutover” → Deployment Slot + Swap.

---

## 🔐 App Service Security Basics

- Managed Identity for secure Azure access
- Authentication/Authorization (Easy Auth)
- Access restrictions (IP allow/deny)
- Private Endpoint for internal-only access

---

## 📦 Container Options (AZ-104 level)

| Service | Best Use |
|--------|---------|
| Web App for Containers | Containerized web apps quickly |
| Azure Container Instances (ACI) | Fast, simple container run |
| AKS | Large-scale orchestration |

🔥 Exam tip: if the requirement is “quick container without orchestration,” choose ACI.

---

## 🌍 App Networking Notes

- App Service can integrate with VNets (outbound scenarios)
- Private Endpoint secures inbound access
- DNS/private resolution may be required when using private access

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Deploy a web app
- Create deployment slot
- Test swap process
- Deploy a simple containerized app

---

## 🔧 Portal Steps

### 1. Create App Service Plan
Name: asp-day6

---

### 2. Create Web App
Name: app-day6

---

### 3. Add Deployment Slot
Slot: staging

---

### 4. Configure App Setting
Add environment variable and validate in staging

---

### 5. Swap Slots
Swap staging → production

---

### 6. Deploy Container (Optional Advanced)
Use ACI or Web App for Containers for a sample image
