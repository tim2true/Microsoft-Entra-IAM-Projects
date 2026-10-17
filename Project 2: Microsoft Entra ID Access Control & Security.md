# Project 2: Microsoft Entra ID Access Control & Security

DISCLAIMER: If you've managed to finish the first project, continue to use the same fictional users, departments, and security groups. Remember that you have a user that should be disabled as well. Use a separate, clearly labeled test account only if you need an enabled account to test a contractor sign-in scenario. Do not enable the user just to make a test pass too. If you never completed the 1st project, I suggest you go back to do so since this is considered a continuation.  

Before starting, confirm that you are in your lab tenant and not your employer's or school's production directory. 

# Task 1: Configure Authentication Methods

To achieve this step, first review your existing groups. You can do this by:
1. Signing in to the Microsoft Entra admin center.
2. Going to Entra ID → Groups → All groups.

From here, you should go into your IT security group. Select Members and verify that you have 2 users from the previous project in the group.

You'll use this group as the pilot group for this authentication lab. 

Later in this project, we'll use the actual 'Security' group to evaluate the administrative security policy design.

# Step 2: Inspect Authentication Methods

1. Navigate to Entra ID → Authentication methods → Policies.

2. Review the methods listed in your tenant, such as:
  - Microsoft Authenticator
  - SMS
  - Voice calls
  - FIDO2 security keys/passkeys, where available
  - Temporary Access Pass, where available

3. Select Microsoft Authenticator.

4. Review whether the method is enabled and which users or groups it targets.

5. If your lab permits changes, configure the policy to target your IT security group rather than all users.

6. Save the change only if the portal permits the scoped configuration and you understand its impact.

This is how it should look after following those steps. 

<img width="1325" height="667" alt="Screenshot 2026-10-17 at 10 45 10 AM" src="https://github.com/user-attachments/assets/6baf78a0-0b1f-4db3-a88e-93865ac43166" />


