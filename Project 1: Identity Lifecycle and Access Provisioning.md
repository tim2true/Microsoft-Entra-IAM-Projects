# Step 1: Generate Your Test Identities

Create 5 fictional employees for your project as test records and not actual real people. For their actual usernames, you must use a domain verified in your 
Entra tenant. 
For example, if your tenant domain is contosolab.onmicrosoft.com, Maya's UPN would be maya.chen@contosolab.onmicrosoft.com.

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
By doing this, you'll go into the Entra Admin center, navigate to Entra ID, then Groups, and finally All Groups.
Select New group, then make sure the Group Type is set to Security. Create the group, fill in name and description, and leave "Microsoft Entra roles can be 
assigned to the group" as disabled.
Leave the membership type to Assigned and leave the initial membership of owners and members blank to add users separately for this project. From there, 
click on Create and repeat to do the same for the other groups. 

This is what my example looks like: 
