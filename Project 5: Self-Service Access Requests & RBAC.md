# Project 5 — Self-Service Access Requests & RBAC (Role-Based Access Control)
In this project, we'll learn how to demonstrate the following:

• RBAC

• Self-service access requests

• Access packages and entitlement management

• Access request testing and exception handling

• Manager and application-owner approvals

But first things first, again we'll be using the same users and groups from the previous projects.

# Task 1: Design a RBAC Access Model

For this specific step, I'll help out with this. For the users in their respective groups, we'll continue to keep them under the roles they were given in your
fictitious business and the permissions that go with them as well. 

For the next step, we're going to use a scenario for this project. I'll be using a member of my own Finance group, her name is Maya Chen. 
You can follow below with the listed information I use and just remix it for your own project purposes.

• Requestor: Maya Chen.

• Requested resource: Finance reporting access.

• Access package: AP-Finance-Reporting-Access.

• Security group: SG-FIN-Employees.

• Business justification: Maya needs access to financial reporting resources to perform her Financial Analyst responsibilities.

• Approval: Manager approval followed by application-owner approval.

• Access duration: 90 days.

• Review: Quarterly, where supported.

# Task 2: Prepare the Users for Approval Workflows

For this exercise, we'll use your existing administrator account as the simulated manager and application owner. 
Because you're the only reviewer, this is a demonstration of a two-stage workflow, not independent approval by two different people.

First step is to set your selected user's manager attribute.

1. Open Microsoft Entra admin center.
2. Navigate to Identity → Users → All users.
3. Search for your selected user.
4. Open their account.
5. Select Properties.
6. Find the Job information section.
7. Locate Manager.
8. Select your administrator account as the selected user's manager.
9. Save the changes.

Make sure you record the application owner as your account for your reporting access package. 
The way we'll document it is like this:

• Application owner: Your administrator account.

• Business resource: Finance reporting.

• Resource group: SG-FIN-Employees.

• Approval responsibility: Validate the business need for Finance access.

# Task 3: Create an Entitlement Management Catalog
A catalog is a container that holds resources and access packages. We'll create one for our security group.
Usually, Entitlement Management access packages require Microsoft Entra ID Governance or Microsoft Entra Suite licensing for the users, but if you had encountered licensing restrictions before this part, spend time checking on the configuration.
Let's get to creating our catalog.

First step is to open Entitlement Management. 
Open the Entra admin center.
Navigate to ID Governance → Entitlement management → Catalogs.
Select + New catalog.

You'll configure your catalog to your own liking when it comes to the name and description. Everything else, leave it default, then click Create.

From there on, you'll open up the catalog you've created. 
Select Resources.
Select + Add resources.
Choose Groups and Teams.
Search for the group your specific user is in.
Select the group.
Select Add.

This what it should look like for you, but from my own configuration and POV.
<img width="1284" height="523" alt="Screenshot 2026-11-17 at 10 43 32 PM" src="https://github.com/user-attachments/assets/135e731d-9349-4796-8a92-0e915a8a7182" />

# Task 4: Create the Access Package
