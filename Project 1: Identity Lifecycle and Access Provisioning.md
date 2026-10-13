# Step 1: Generate Your Test Identities

Create 5 fictional employees for your project as test records and not actual real people. For their actual usernames, you must use a domain verified in your 
Entra tenant. 
For example, let's say you have an employee named Johnathan Taylor. If your tenant domain is contosolab.onmicrosoft.com, Johnathan's UPN would be johnathan.taylor@contosolab.onmicrosoft.com.

To find your tenant domain:
1. Open the Microsoft Entra admin center.
2. Sign in using your authorized lab administrator account.
3. Open Entra ID.
4. Select Overview.
5. Find the Primary domain or available tenant domains.
6. Record the domain you will use in your lab documentation.
Use the actual domain displayed in your tenant; contosolab.onmicrosoft.com is only an example.

# Step 2: Create the Security Groups
You will create groups that represent department access. In an IAM environment, groups make access easier to manage consistently instead of assigning every 
permission individually.

For this step, you'll create 5 security groups. Create a security group for IT, Sales, Security, Finance, and Contractors.
1. By doing this, you'll go into the Entra Admin center, navigate to Entra ID, then Groups, and finally All Groups.
2. Select New group, then make sure the Group Type is set to Security. Create the group, fill in name and description, and leave "Microsoft Entra roles can be assigned to the group" as disabled.
3. Leave the membership type to Assigned and leave the initial membership of owners and members blank to add users separately for this project.
4. From there, click on Create and repeat to do the same for the other groups. 

After creating each security group, this is what a overview should look like for one of the many individual groups you've worked on.
<img width="1576" height="669" alt="Screenshot 2026-10-13 at 4 53 57 PM" src="https://github.com/user-attachments/assets/bac0d708-48ac-47ad-94c2-ef7b6f7c3e5c" />

# Step 3: Create the Users

After generating your employees, we'll create 3 of those employees for this step. 
1. You'll create your users by navigating to Entra ID, then to Users, and finally All Users. 
2. From there, you'll select on New user, then click on Create new user.
3. Fill out information pertaining to your generated user and what department you'll have them in. What's more important is that you save the generated 
temporary password that is being used for those users as well. Do not save it in anything that is used in your lab environment.

Once you've created your users, head back to the Groups tab and add the members to the groups you desire them to be in. 
To do this, you go from Groups -> All groups, then select the appropriate group. 
From there, select Members and click on the Users tab to make it easier to find the user you created. Then, add the member by clicking select. 

Here's an example of a user I've created in the perspective group I assigned them into after following those steps. 
<img width="1579" height="670" alt="Screenshot 2026-10-13 at 5 17 57 PM" src="https://github.com/user-attachments/assets/ab5ff429-7fcb-46a2-a315-e63867777244" />

# Step 4 - 6: Onboard, Transfer, & Offboard

If you've reached these steps with no issues, go ahead and create the last 2 users. We'll use generated tickets to simulate how an IAM analyst carry on their tasks with the users that are in the infrastructure.
```
IAM ticket #IAM-001
Pending Work

Request type: New employee onboarding
Request: HR reports that one of the new created users is joining Contoso Financial Services as a Financial Analyst in Finance.
Requested start date: Use today's date in your lab record.
Requested access: Finance employee group membership.
```
From here, take one of the last 2 new created users that haven't been assigned to a group and onboard them to the Finance group. 
Verify that the user is onboarded properly into the group and this fictitious ticket is completed. 

```
IAM ticket #IAM-002
Pending work

Request type: Department transfer
Request: User is transferring from Sales to IT Operations.
Old access: SG-SALES-Employees
New access: SG-IT-Operations
```
For this ticket, you'll have to go the User's account and confirm that the user is found within the Sales group. From there, you have to remove the user
from the group and verify that the user isn't in the Sales group anymore. Then, you'll return to the user that you removed from the Sales group and add
them into the IT group. Make sure you change their job title if you have it listed and save the changes before doing so. Finally, just verify that the transfer has been successfully completed.

```
IAM ticket #IAM-005
High priority

Request type: Contractor termination
Request: The last user's fictional contract has ended. The authorized requester confirms that access must be revoked.
Current access: SG-EXT-Contractors
Required outcome: Block new sign-ins, revoke sessions, remove applicable access, and preserve the account record for the lab's review.
```
For this ticket, the last user you've created needs to be assigned to the Contractors group. Make sure their account is enabled and you've recorded the temporary password for the user. Once you've created the account and assigned them to the group, verify their account status and that they're in the Contractors group. From here, you'll go back into Users and find the last user you've created. Open up the properties tab once you've selected the user and disable their account by unchecking the account enabled box. Save the change and verify that the account has been disabled. You'll head back to the overview of the user and select Revoke sessions. After doing so, you'll end up removing the user from the Contractors group, then finally you'll verify if the user has been completely offboarded. Do not delete the account. 

Congratulations, you've completed your first task as an IAM analyst!
