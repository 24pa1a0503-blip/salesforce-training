# Day 2: Platform Basics

## 1. What is the Salesforce Platform?

Salesforce Platform is a cloud-based platform that lets businesses build applications,manage customer data, and automate processes--all in one place.

## 2. Core Concepts Explained

* **App:** Imagine an App as a dedicated workspace or a folder for a specific job. It’s simply a collection of items (like tabs and dashboards) grouped together to help users complete a specific business process (e.g., a "Recruiting" app or a "Sales" app).
* **Object:** If Salesforce is a giant Excel workbook, an Object is a single spreadsheet tab within it. It’s a database table that stores a specific kind of information. For example, a "Student" object holds all data related to students.
* **Tab:** A Tab is the clickable shortcut at the top of your screen. It is the user interface element that lets you actually click into and view the data stored inside an Object. 

---

## 3. Configuration vs. Coding

* **Configuration (Clicks):** This is like building with Lego blocks. You use Salesforce's drag-and-drop tools and menus to build forms, automate rules, and create data tables. You are building the system *without* writing a single line of code.
* **Coding (Code):** This is like 3D printing your own custom Lego blocks. When the standard point-and-click tools aren't enough to handle a highly complex or unique business requirement, developers write actual code (like Apex or JavaScript) to make it happen.

---

## 4. Real System Thinking: College Admission System

Based on my standard object mapping, here is how I would design the system into an actual Salesforce App:

* **App Name:** `Admissions Hub`
* **Objects Inside It:**
    * `High Schools` *(Standard Account Object)*: The institution the student is coming from.
    * `Students` *(Standard Contact Object)*: The individual person applying for a degree.
    * `Applications` *(Standard Opportunity Object)*: The specific "deal"—tracking the student from "Applied" to "Admitted" or "Enrolled."
    * `Prospective Students` *(Standard Lead Object)*: Someone who filled out an inquiry form but hasn't applied yet.
    * `Campus Tours` *(Custom Object)*: A custom table to track when a prospective student visits the campus.
* **How Users Interact With It:**
    * An **Admissions Recruiter** logs into the `Admissions Hub` app and clicks the `Prospective Students` tab to check for new web inquiries.
    * They call a prospective student, and when the student decides to apply, the recruiter converts them into a `Student`.
    * An **Admissions Reviewer** uses the `Applications` tab to update the student's status, dragging their application stage from "Under Review" to "Admitted."

---

## 5. Screenshots from Trailhead

<table>
  <tr>
    <td width="50%">
      <b>Contact Object Details</b><br>
      <img src="Screenshot 2026-05-09 170442.png" alt="Contact Object Details">
    </td>
    <td width="50%">
      <b>Selecting Field Type</b><br>
      <img src="Screenshot 2026-05-09 181251.png" alt="Selecting Field Type">
    </td>
  </tr>
  <tr>
    <td width="50%">
      <b>Creating Loan Amount Field</b><br>
      <img src="Screenshot 2026-05-09 181328.png" alt="Creating Loan Amount Field">
    </td>
    <td width="50%">
      <b>VS Code CLI Output</b><br>
      <img src="Screenshot 2026-05-09 192004.png" alt="VS Code CLI Output">
    </td>
  </tr>
  <tr>
    <td width="50%">
      <b>Dreamhouse Project Structure</b><br>
      <img src="Screenshot 2026-05-09 192516.png" alt="Dreamhouse Project Structure">
    </td>
    <td width="50%">
      <b>Org Authentication Success</b><br>
      <img src="Screenshot 2026-05-09 194147.png" alt="Org Authentication Success">
    </td>
  </tr>
  <tr>
    <td width="50%">
      <b>Importing Custom Object</b><br>
      <img src="Screenshot 2026-05-09 194933.png" alt="Importing Custom Object">
    </td>
    <td width="50%">
      <b>Viewing House Records</b><br>
      <img src="Screenshot 2026-05-09 195203.png" alt="Viewing House Records">
    </td>
  </tr>
  <tr>
    <td width="50%">
      <b>Creating Lightning App - Branding</b><br>
      <img src="Screenshot 2026-05-09 195647.png" alt="Creating Lightning App - Branding">
    </td>
    <td width="50%">
      <b>Creating Lightning App - Navigation</b><br>
      <img src="Screenshot 2026-05-09 195954.png" alt="Creating Lightning App - Navigation">
    </td>
  </tr>
</table>
