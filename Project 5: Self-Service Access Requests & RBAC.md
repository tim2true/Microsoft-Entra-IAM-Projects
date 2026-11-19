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
You will now create the package that employees will request upon.

You will create the new access package by:
1. Navigating to ID Governance → Entitlement management → Access packages.

2. Select + New access package.

Under Basics tab, you can give your access package a name and description of your own liking, but make sure the catalog is under the created catalog you've made.

Next, go into Resource roles.

You will select the resource by clicking on Groups and Teams, the custom group you've made for this catalog, and change the role from "Select Role" into "Member." This is how it should look like. 
<img width="1310" height="470" alt="Screenshot 2026-11-19 at 10 57 52 AM" src="https://github.com/user-attachments/assets/fb8d4bd6-f77e-464f-aafa-b70b3a268247" />

We'll move into the Requests section and change these configuration settings:

• Who can get access: For users ...

• Select Specific Scope: Specific users and groups

• Who can request access: Leave it on Admin if you want your administration accounts to dish out the access as well, but my recommendation is to put it on Self. 

Now these settings are important for the approval workflow, below configure the settings to these options:

• Require Justification: Yes

• Require Approval: Yes

• How many stages: 2

By default, you'll see 2 stages, one being the "manager as approver" approval and the other one being "choose specific approvers" application.

For both of these stages, I chose both of my administrator accounts, leaving every other settings between the two stages default.

<img width="1024" height="662" alt="Screenshot 2026-11-19 at 11 19 00 AM" src="https://github.com/user-attachments/assets/62047fa4-8778-4c2e-a7bc-fd1abe015d37" />

<img width="1068" height="664" alt="Screenshot 2026-11-19 at 11 19 22 AM" src="https://github.com/user-attachments/assets/8b61d6d9-f19f-4a42-9026-b841c0408c28" />

<img width="883" height="668" alt="Screenshot 2026-11-19 at 11 19 36 AM" src="https://github.com/user-attachments/assets/1909aa15-e970-4e93-a178-c1f767ef23c4" />

Soon as we finish this Requests tab, we'll jump over into the Lifecycle tab.

Under the Lifecycle tab, the only change we'll make to this is the number of days where the access package assignments expire. Change the default 365 days to 90. After that, make sure that "approval for extensions" and "allow users to extend access" settings are set to yes.

<img width="1198" height="663" alt="Screenshot 2026-11-19 at 11 18 25 AM" src="https://github.com/user-attachments/assets/66e823d7-8375-47c3-91ce-0f1d7df2fd07" />

# Task 5 & 6: Submit a Self-Service Access Request & Complete Approval Workflow
From here, we'll test the workflow with the user from the selected group.

You'll do this by going into the [My Access Portal](https://myaccess.microsoft.com)

Sign into the user that's in the group with the catalog and access package.

Navigate to Access packages

Find the access package you've created, open it, and select Request access.

Make sure that you've selected "Myself" with the user you're as, and give the business justification like needing the access to do the responsibilities as the role. 

After you submit, this is how it should look.
<img width="1321" height="448" alt="Screenshot 2026-11-19 at 12 08 38 PM" src="https://github.com/user-attachments/assets/6523ca26-5be3-4d02-8c97-aeca4d5db9dd" />

Now after requesting to get the access package, log into My Access through your administrator account. 

Navigate to Approvals, open the request and review the business justification you've made under the user. 

Approve it as the manager and application-owner with your own justification. 

# Task 7: Testing Unauthorized & Conflicting Access Requests
An IAM analyst must verify that the request policy does not give everyone access to every resource.

For our test case, we'll check to see that every other member in our directory is not able to request for the access package. 

Once you log into each and every user, active or disabled, verify that they can't request or you can't even log into their account due to being disabled.

Access requests are restricted according to business roles. Employees outside Finance are not eligible for the Finance reporting access package under the configured request policy. This reduces unnecessary access and helps enforce least privilege and separation of duties.

# Task 8: Configure Access Reviews and Expiration
This connects this project back to Project 4.
