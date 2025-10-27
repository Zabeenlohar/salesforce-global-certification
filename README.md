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

### 📅 Day 4 - [20-10-2025]
**Topic:**  
*Apex Testing*

**What I Did:**
- Completed the Apex Testing module (earned 1,500 points).
- Covered three major sections:
  1. Get Started with Apex Unit Tests
  2. Test Apex Triggers
  3. Create Test Data for Apex Tests

 ---

 #### 🔹 Get Started with Apex Triggers
**What I Learned:**
- The Apex Testing Framework helps ensure that classes and triggers work correctly.
- Apex unit tests:
  - Validate functionality and prevent regression bugs.
  - Are required for code deployment (at least 75% code coverage).
  - Improve app quality and maintainability.
- Learned test class and method syntax using @isTest.
- Understood the importance of positive and negative test cases, boundary testing, and assertions (System.assertEquals).

**Practiced Examples:**
- Created a simple class TemperatureConverter that converts Fahrenheit to Celsius.
- Wrote its test class TemperatureConverterTest with multiple test methods for different scenarios (freezing, boiling, warm, and negative temperatures).
- Verified successful test runs and explored code coverage results in the Developer Console.
- Simulated a failed test using incorrect expected values to understand test failures.

**Key Takeaways:**
- Write comprehensive tests — not just for coverage, but for quality validation.
- Rerun tests after every code change to update coverage results.
- Code coverage improves when all logic branches (e.g., if-else conditions) are tested.
   
---

 #### 🔹 Test Apex Triggers
 **What I Learned:**
 - Before deploying a trigger, it must be tested using unit tests.
 - Learned to create and test a trigger that prevents account deletion when related opportunities exist.

**Example Practiced:**
- Created the AccountDeletion Trigger:
  
```apex
trigger AccountDeletion on Account (before delete) {
for(Account a : [SELECT Id FROM Account WHERE Id IN (SELECT AccountId FROM Opportunity) AND Id IN :Trigger.old]) {
Trigger.oldMap.get(a.Id).addError('Cannot delete account with related opportunities.');
}
}
```

- Tested it using TestAccountDeletion class that:
  - Inserts a test account and related opportunity.
  - Attempts to delete the account.
  - Asserts that deletion fails with the correct error message.

**Concepts Learned:**
- Using Test.startTest() and Test.stopTest() to isolate test execution and governor limits.
- Ensuring triggers handle single record, bulk, and negative cases.
- Importance of testing both valid and invalid scenarios to ensure robust trigger logic.

---

#### 🔹 Create Test Data for Apex Tests
**What I Learned:**
- Instead of creating test data repeatedly, use a test utility class to generate reusable test data.
- Test data is rolled back automatically after test execution, so the org remains clean.
- Created a utility class TestDataFactory with a reusable method to create accounts and opportunities.

**Practiced Example:**

```apex
  @isTest
public class TestDataFactory {
    public static List<Account> createAccountsWithOpps(Integer numAccts, Integer numOppsPerAcct) {
        List<Account> accts = new List<Account>();
        for(Integer i=0;i<numAccts;i++) {
            accts.add(new Account(Name='TestAccount' + i));
        }
        insert accts;

        List<Opportunity> opps = new List<Opportunity>();
        for(Account acct : accts) {
            for(Integer k=0;k<numOppsPerAcct;k++) {
                opps.add(new Opportunity(
                    Name=acct.Name + ' Opportunity ' + k,
                    StageName='Prospecting',
                    CloseDate=System.today().addMonths(1),
                    AccountId=acct.Id
                ));
            }
        }
        insert opps;
        return accts;
    }
}
```

**Updated Test Class Example:**
- Used TestDataFactory.createAccountsWithOpps(1,1) to create test data efficiently.
- Reduced repetitive setup code and made tests cleaner.

---

#### 💡 Key Takeaways:
- Unit tests ensure code quality, maintainability, and safe deployments.
- Always test for multiple input scenarios and logical branches.
-  Use test data factories to simplify and standardize data creation.
-  Remember to include Test.startTest() and Test.stopTest() for accurate test execution.

---

#### 🧩 Skills Gained:
- Writing and executing Apex test classes and methods.
- Achieving and analyzing code coverage
- Testing Apex triggers for various data operations.
- Building test utility classes for reusable test data.
- Writing assertions for expected outcomes and validation.

---

**Reflection:**
Today’s module gave me a deep understanding of Apex Testing — one of the most crucial parts of Salesforce development. I learned not just to test for deployment but to build tests that ensure long-term reliability. Feeling much more confident about writing efficient, reusable, and scalable test methods for real-world scenarios! 🚀 

---














  














