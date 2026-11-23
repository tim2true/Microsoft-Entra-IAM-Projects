# Project 6: Privileged Access Management with Microsoft Entra PIM
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
```
Maximum Activation Duration = 2 hours
On activation, require = Azure MFA
Require Justification = Yes
Require Ticket Information = Yes
Require Approval = Yes
Approver = YOUR administration account
Notifications = Enabled
```
Save your changes after completing it.

Test one of your user's activation by opening a separate browser or private browsing session. Sign into their accounts using the [Microsoft MyAccount Link](https://myaccount.microsoft.com?). Go into the My Access tab and find Roles. You'll finish doing your MFA, and navigate over to Entra Roles. Find the appropriate role you've assigned the user and select Activate. Enter a sample ticket number, and enter your justification for requiring the role such as needing it to troubleshoot a user account, etc. After completing your justification, submit the request.

Head back to Entra admin center and sign in as the approver which in this case is your administrator account. Navigate to PIM, then Approve requests. Find your user's justification request, then review their justification and requested duration. Approve the request and head back to the user's session. From there, you should verify that the Helpdesk Administrator or Security Reader role is active for them. 

<img width="1310" height="660" alt="Screenshot 2026-11-21 at 6 06 58 PM" src="https://github.com/user-attachments/assets/73884d23-663d-406f-a74c-1e2e8c47dac4" />

<img width="1575" height="460" alt="Screenshot 2026-11-21 at 6 13 00 PM" src="https://github.com/user-attachments/assets/8368bfd9-38af-4b83-af4a-b183ead39079" />

# Task 5: Configure PIM for Groups
For this goal, we'll be demonstrating just-in-time membership in an existing security group. We'll reuse our IT group.

Head back to the PIM tab by heading to Identity Governance, then PIM. We'll select on the Groups tab. Find the IT group then select it, from there, click on Settings under the Manage side tab. The same settings we gave the roles for our selected users, we'll do the same under Member settings.

After saving the settings, we'll go back into the sidebar and select Assignments as the same group under PIM.

We're going to configure and test the membership. So from here, click on Add assignments and choose Member under Select Role. Select one of your IT guys and choose Eligible once you've clicked next. Submit the assignment from there. 

Now since your user is already a member of the IT group, if you want to demonstrate JIT membership, you would need to remove his standing membership before relying on the eligible assignment. Document the current membership and make sure the group is not controlling access you need to preserve. 

Head back into Microsoft MyAccount, under Roles in My Access, check the Groups tab to see if the group membership for your IT group shows up under the same test user. Activate, submit a business justification, then submit request. Go through the same process of approving it, then verify it. 

# Task 6: Review Privileged Access
The goal in this task is to perform an access certification for privileged role assignments. This is almost similar to Project 4, but it isn't quite the same.

We'll navigate back to the PIM section, but head under Microsoft Entra roles again. Under Manage, select Access reviews and then New. 

We're going to use these settings for the project purposes:
```
Start date: The day you've set this certification up
Frequency: Quarterly
Duration: 7 days
End: Never
Users scope: Users and Groups
Roles: Helpdesk Administrator and Security Reader
Assignment type: All active and eligible assignments
Reviewer: Your administrator account
```
Under "Upon completion settings" and "Advanced settings," make sure these settings are as the following:

If reviewers don't respond: No Change

Require reason on approval: Enable

Mail notification and reminders (Both): Enable

Auto apply results: Keep enable if you want to approve/deny decisions automatically applied.

Now it's time to perform the reviews. You can open the review and do it from clicking Review Access from the PIM sidebar. Both reviews should show up for both roles. Open it up, enter a justification, and approve or deny based on the users you've set to received these privileged roles. 

For example, this is how one of my reviews look like for my Security Reader, Taylor Morgan. 

<img width="1247" height="626" alt="Screenshot 2026-11-21 at 11 25 26 PM" src="https://github.com/user-attachments/assets/b0129b6b-2121-43bf-98e1-a5bf22e6bfa9" />

There you have it, Project 6 is completed!
