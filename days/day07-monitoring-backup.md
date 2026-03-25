# AZ-104 Bootcamp – Day 7  
## Governance & Cost Management (HIGHLY TESTED – SCENARIO HEAVY)

---

# 🔥 Why This Matters

This is where Microsoft tests **decision-making**.

You will see questions like:
- “How do you enforce standards?”
- “How do you control cost?”
- “How do you prevent bad deployments?”

👉 This is NOT technical — this is CONTROL & POLICY thinking

---

# 🧠 Day 7 Objectives

- Master Azure Policy (VERY TESTED)
- Understand Initiatives
- Learn Cost Management tools
- Use Tags effectively
- Apply Governance strategies

---

# ⏱️ Time Plan

| Block | Time |
|------|------|
| Concepts | 2–3 hrs |
| Hands-on Labs | 3–4 hrs |
| Practice + Review | 1–2 hrs |

---

# 🔹 STEP 1 – TEACH (Exam-Focused)

## 📜 Azure Policy (CORE GOVERNANCE TOOL)

Azure Policy = **enforces rules**

---

## 🔥 RBAC vs Policy (CRITICAL)

| Feature | Purpose |
|--------|--------|
| RBAC | WHO can access |
| Policy | WHAT is allowed |

---

## 🧠 Policy Effects (VERY TESTED)

| Effect | Meaning |
|-------|--------|
| Deny | Block deployment |
| Audit | Log violation |
| Append | Add property |
| DeployIfNotExists | Auto-fix |

---

## 🔥 EXAM KEY

- Stop something → Deny  
- Monitor → Audit  
- Fix automatically → DeployIfNotExists  

---

## 📦 Policy Scope

Can apply at:
- Management Group
- Subscription
- Resource Group

---

## 🧠 Initiatives

Group of policies

👉 Used for:
- Compliance (e.g., security baseline)

---

## 🔥 EXAM TRICK

If question says:
“Apply multiple policies together”

👉 Answer = Initiative

---

## 🏷️ Tags

Used for:
- Cost tracking
- Organization

---

## 🔥 IMPORTANT

Tags DO NOT enforce rules  
👉 Policy enforces

---

## 💰 Cost Management

Used to:
- Track spending
- Set budgets
- Forecast usage

---

## 🧠 Key Tools

| Tool | Purpose |
|------|--------|
| Budgets | Limit spending |
| Alerts | Notify overuse |
| Cost Analysis | Breakdown costs |

---

## 🔥 EXAM RULE

Budget does NOT stop spending  
👉 Only alerts

---

## 📊 Azure Advisor

Gives:
- Cost recommendations
- Performance suggestions

---

## 🔥 EXAM TRICK

“Optimize cost automatically”

👉 Advisor + Lifecycle + Right-sizing

---

## 🧠 Governance Strategy

Use together:
- Policy
- RBAC
- Tags
- Budgets

---

# 🔹 STEP 2 – HANDS-ON LAB

## 🎯 Scenario

You will:
- Enforce tagging
- Restrict regions
- Track cost
- Create budgets

---

## 🔧 Portal Steps

### 1. Create Policy

Policy: Require tag "Environment"

---

### 2. Assign Policy

Scope: Subscription

---

### 3. Test Policy

Create resource WITHOUT tag  
👉 Should fail

---

### 4. Create Initiative

Combine:
- Require tag
- Restrict region

---

### 5. Assign Initiative

Apply at subscription level

---

### 6. Create Budget

Set monthly budget

---

### 7. Create Alert

Notify at 80%

---

### 8. Use Cost Analysis

Review spending breakdown

---

# 💻 CLI COMMANDS

Assign policy:

az policy assignment create \
  --name require-tag \
  --policy <policy-id> \
  --scope /subscriptions/<id>

---

Create budget:

az consumption budget create \
  --amount 1000 \
  --time-grain monthly \
  --name budget-day7 \
  --resource-group rg-day1-core

---

# 💻 PowerShell COMMANDS

New-AzPolicyAssignment `
  -Name "require-tag" `
  -Scope "/subscriptions/<id>"

---

# 🔹 STEP 3 – EXAM TRAPS

❌ Trap 1  
Thinking tags enforce rules  
👉 They DO NOT

---

❌ Trap 2  
Budget stops spending  
👉 It DOES NOT

---

❌ Trap 3  
RBAC used instead of Policy  
👉 RBAC = access  
👉 Policy = enforcement

---

❌ Trap 4  
Multiple policies separately applied  
👉 Use Initiative

---

❌ Trap 5  
Wrong policy effect  
👉 Deny vs Audit vs DeployIfNotExists

---

# 🔹 STEP 4 – PRACTICE QUESTIONS

Q1  
Enforce tag requirement:

A. RBAC  
B. Policy  
C. NSG  
D. Lock  

Answer: B

---

Q2  
Group multiple policies:

A. Tag  
B. Initiative  
C. RBAC  
D. Budget  

Answer: B

---

Q3  
Stop deployment without tag:

A. Audit  
B. Deny  
C. Append  
D. Lock  

Answer: B

---

Q4  
Notify when cost exceeds threshold:

A. Policy  
B. Budget  
C. NSG  
D. Disk  

Answer: B

---

Q5  
Best tool for cost optimization:

A. Advisor  
B. NSG  
C. RBAC  
D. DNS  

Answer: A

---

Q6  
Who can access resources:

A. Policy  
B. RBAC  
C. Budget  
D. Tag  

Answer: B

---

Q7  
Automatically fix non-compliant resources:

A. Deny  
B. Audit  
C. DeployIfNotExists  
D. Lock  

Answer: C

---

# 🧠 MUST MEMORIZE

- RBAC = WHO  
- Policy = WHAT  

- Deny = block  
- Audit = monitor  
- DeployIfNotExists = fix  

- Budget = alert only  

---

# 🔁 Reinforcement

Repeat:

- Policy vs RBAC
- Budget behavior
- Initiative purpose

---

# 🚨 Homework

1. Create policy
2. Assign it
3. Break deployment
4. Create budget
5. Answer:

👉 What actually enforces rules?  
👉 What only notifies?

---

# ⏭️ Next: Day 8 (Review + Weak Area Reinforcement)

- Mixed scenarios
- Cross-topic questions
- Exam-style thinking
