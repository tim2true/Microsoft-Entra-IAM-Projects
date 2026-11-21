This project builds on the first five projects by moving from managing ordinary employee access to managing privileged administrative access.

If you made it this far, you know we're going to use the same users and security groups. 

Before we start, make sure that you have the appropriate licensing for having eligible assignments, approvers, and reviewers. (Microsoft Entra ID P2 or Microsoft Entra ID Governance)

# Task 1 & 2: Privileged Role Inventory & Least-Privilege Planning
These tasks are together so we can identify which accounts have administrative permissions, determine which permission each employee needs without giving them the excessive administrative access, and finally conclude whether the permissions are justified.

First, we'll check the existing administrative role assignments. You'll do this by opening Identity Governance, then going to Privileged Identity Management. After that, select Microsoft Entra roles, then Assignments. Go through the 3 tabs of active, eligible, and expired assignments. Record the users, roles, assignment types, and expiration dates.

Then from there, we'll head back into the Entra ID sidebar and go to Roles & admins. Open the roles like Global Administrator, Privileged Role Administrator, User Administrator, Helpdesk Administrator, and Security Reader. Make sure you review their assignments because this is essential to know that standing administrative access may not be managed through PIM. 

Create your inventory with the users, their current roles, and if they even had privileged access to begin with or not. We'll be using the roles above for this project for our IT guys. 

# Task 3: Configure PIM Eligible Role Assignments
Our goal within this task is making our IT guys eligible to active their separate administrative roles, instead of permanently holding those privileges.

Our first step for the 2 IT guys is to assign Helpdesk Administrator and Security Reader to them, but only one role for each. 

We'll navigate to Identity Governance then to Privileged Identity Management again. Select Microsoft Entra roles, then roles. For the two roles, search for them and open it. From there, you'll open Add assignments and select the members you've decided to hand the role out to. After doing so, make sure you go to assignment type and confirm that the type is on Eligible. After your configuration, select Assign.

Here's how they should look after assigning roles.
<img width="1310" height="668" alt="Screenshot 2026-11-21 at 5 46 12 PM" src="https://github.com/user-attachments/assets/80f722f9-0bcc-4328-af7b-a3c0de347276" />
<img width="1314" height="667" alt="Screenshot 2026-11-21 at 5 47 08 PM" src="https://github.com/user-attachments/assets/ec78a423-ee9b-4af9-a3c3-cc628f47e33b" />

# Task 4: Configure Just-In-Time Activation and Approval
The goal of this task is to justify why they need these elevated permissions and to limit how long they can use them.

For both of their roles, we'll configure their settings to be the same. 

1. Open PIM → Microsoft Entra roles.

2. Select Roles.

3. Search for Helpdesk Administrator and/or Security Reader.

4. Open the role.

5. Select Settings.

6. Select Edit.

These are the settings we'll set for the roles:
