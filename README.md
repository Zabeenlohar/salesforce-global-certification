## 📘 Daily Log

### 📅 Day 1 - [14-10-2025]
**Topic:**  
**Salesforce Platform Basics**

**What I Did:**
- Created my Salesforce Developer account.
- Explored Trailhead and started the *Salesforce Platform Basics* module.

**What I Learned:**
- What CRM (Customer Relationship Management) means.
- Key Salesforce features and benefits.
- Types of Salesforce clouds (Sales, Service, Marketing).

**Reflection:**  
Feeling motivated! The interface looks modern and powerful — can’t wait to dive deeper 🌟

### 📅 Day 2 - [15-10-2025]
**Topic:**  
*Salesforce Trailmix & Trailhead Playground Management*

**What I Did:**
- Searched and explored the following courses:
  - Trailmix by **S B**
  - Trailmix by **Smartinternz (Developer)**
  - **Salesforce Developer**
- Completed two modules:
  1. **Salesforce Values: Quick Look**
  2. **Trailhead Playground Management**

**What I Learned:**

**1️⃣ Salesforce Values: Quick Look**
- How Salesforce values drive the platform for change.  
- Salesforce CRM helps deliver excellent customer experiences.  
- Understood the **five core Salesforce values**.  
- Learned how businesses can use Salesforce as a **platform for positive change**.  

**2️⃣ Trailhead Playground Management**
- How to **create a Trailhead Playground** for hands-on practice.  
- The difference between a **Trailhead Playground** and a **Developer Edition Org**.  
- How to **get and rename** Trailhead Playground username and password.  
- Steps to **install apps and packages** in Trailhead Playground.  

**Reflection:**  
Today felt productive! I got familiar with how Salesforce Trailhead works and how to practice hands-on using Trailhead Playground. Excited to explore more technical modules next 🚀  

### 📅 Day 3 - [16-10-2025]
**Topic:**  
*Apex Triggers*

**What I Did:**
- Completed the **Apex Triggers** module (earned 1000 points).  
- Covered two main sections:
  1. Get Started with Apex Triggers  
  2. Bulk Apex Triggers  

---

#### 🔹 Get Started with Apex Triggers
**What I Learned:**
- How to write triggers that execute actions **before or after DML events** like insert, update, delete, and undelete.  
- Understood **trigger syntax** and important **context variables**:
  - `Trigger.new`, `Trigger.old`, `Trigger.isInsert`, `Trigger.isUpdate`, etc.  
- Practiced creating a simple trigger: `HelloWorldTrigger` for the `Account` object.  
- Learned trigger use cases:
  - Automatically creating related **Opportunity** records for new Accounts.  
  - Sending **custom notifications** after record creation.  
  - Preventing **Account deletion** if related Opportunities exist.  
  - Performing **asynchronous callouts** using `@future(callout=true)` methods.  

---

#### 🔹 Bulk Apex Triggers
**What I Learned:**
- Importance of **bulkifying triggers** to handle large data volumes efficiently.  
- Salesforce processes triggers in **batches of 200 records**, so optimization is crucial.  
- Best practices learned:
  - ❌ Avoid SOQL/DML inside `for` loops.  
  - ✅ Use **collections** (`Lists`, `Maps`, `Sets`) to perform operations on multiple records.  
- Practiced examples:
  - Using `WHERE Id IN :Trigger.new` in SOQL queries.  
  - Performing DML operations on collections instead of single records.  
- Enhanced previous triggers (`AddRelatedRecord`, `SoqlTriggerBulk`, `DmlTriggerBulk`) to make them **bulk-safe**.  

---

#### 💡 Key Takeaways:
- Always **bulkify triggers** to avoid hitting governor limits.  
- Keep business logic in **helper classes** for cleaner, reusable code.  
- Use **context variables** smartly to handle multiple trigger events.  
- Handle exceptions with `addError()` for better data integrity.  

---

#### 🧩 Skills Gained:
- Writing and optimizing Apex Triggers.  
- Using SOQL and DML effectively inside triggers.  
- Understanding Salesforce **trigger lifecycle** and **best practices**.  
- Building efficient, scalable automation logic.  

---

**Reflection:**  
Today’s module was really insightful! I learned how triggers automate business logic and how important it is to keep them efficient. Excited to move on to more complex Apex topics 💻⚡  

---
