## 1. What is SOQL?

**SOQL** stands for *Salesforce Object Query Language*. If you have ever used SQL, SOQL is its Salesforce equivalent. It is the language we use to "talk" to the Salesforce database and ask it specific questions. Instead of manually clicking through tabs and lists to find data, we write a SOQL query in our Apex code to instantly retrieve the exact records we need (e.g., "Give me the names of all students with a GPA above 3.5").

---

## 2. What is an Apex Trigger?

An Apex Trigger is a piece of code that acts like a highly sensitive "tripwire" on the database. It executes automatically behind the scenes when a specific event occurs—such as a record being inserted (created), updated, deleted, or undeleted. Triggers allow us to perform custom, complex actions right before or right after the data actually hits the Salesforce database.

---

## 3. Core Differences

### Flow vs. Apex Trigger
* **Flow:** The declarative (point-and-click) way to automate processes. It is great for simple background updates and standard business rules.
* **Trigger:** The programmatic (code) way to automate processes. You use a Trigger when the automation is too complex for a Flow, when you need to process thousands of records simultaneously (bulkification), or when you need to update complex networks of related objects.

### Before Trigger vs. After Trigger
* **Before Trigger:** Fires *before* the record is actually saved to the database. 
  * *Use Case:* Validating data or updating fields on the *exact same record* that the user is trying to save. (Because the record isn't saved yet, it doesn't have a Salesforce ID).
* **After Trigger:** Fires *after* the record is saved to the database. 
  * *Use Case:* Creating or updating *other related records* (because the original record now has a permanent Salesforce ID that you can link to), or sending emails.

---

## 4. My Trigger Use Cases (Campus Connect System)

Here are 5 ways I would use Apex Triggers to automate complex logic in our College System:

1. **Auto-Assign Student Email (Before Insert):** * *Logic:* Before a new `Student__c` record is saved, the trigger looks at their First Name and Last Name, generates a standardized university email (e.g., `j.smith@campusconnect.edu`), and fills out the Email field automatically.
2. **Freshman Schedule Generator (After Insert):** * *Logic:* After a new `Student__c` is created with the status "Freshman", the trigger automatically generates 4 default `Enrollment__c` junction records, instantly registering them for standard Gen-Ed classes.
3. **Professor Department Transfer (After Update):** * *Logic:* If a `Professor__c` record is updated to belong to a new `Department__c`, the trigger automatically goes and finds all of their active `Course__c` records and updates the "Budget Code" field to match the new department.
4. **Course Capacity Lock (Before Update):** * *Logic:* Before an `Enrollment__c` record status changes from "Waitlist" to "Enrolled", the trigger counts how many students are currently in the course. If the course is exactly at maximum capacity, it throws a custom error blocking the enrollment.
5. **Prevent Active Class Drop (Before Delete):** * *Logic:* Before a user can delete an `Enrollment__c` record (dropping a class), the trigger checks the `Course__c` start date. If the term has already started and the "Drop Deadline" has passed, the trigger blocks the deletion and tells the user they must receive Dean approval.

---

## 5. SOQL Query Examples

Here is how I would translate business questions into English-style query ideas for the database:

* **Idea 1 (Basic Retrieval):** *"Get the First Name, Last Name, and current GPA of all Students who have the 'Honor Roll' checkbox checked."*
* **Idea 2 (Relationship Filtering):** *"Find all Course records taught by 'Professor Jane Doe' that are worth 4 or more credits."*
* **Idea 3 (Sorting & Timeframes):** *"Give me the names and Enrollment Dates of all Students who were enrolled in the last 30 days, ordered by their GPA from highest to lowest."*
* **Idea 4 (Aggregating Data):** *"Count the total number of Active Enrollments grouped by the Department (e.g., How many total students are taking Science classes vs. Arts classes?)."*

---

## 6. Reflection: Why Enterprise Systems React Automatically

In a massive enterprise setting like a university, data changes constantly. A student drops a class, a tuition payment clears, a professor changes their office hours. 

If the system relied on humans to manually react to every single one of these changes—like remembering to email the next student on the waitlist when a seat opens up—the university would grind to a halt. There would be constant human error, massive delays, and compromised data integrity.

Enterprise systems *must* react automatically to data changes because **real-time accuracy is the lifeblood of the business**. Automated triggers ensure that business logic is executed perfectly, instantly, and at scale, allowing staff to focus on actually helping students rather than doing data entry.
