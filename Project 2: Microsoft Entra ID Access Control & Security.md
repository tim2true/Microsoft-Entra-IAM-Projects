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

# Step 1: Inspect Authentication Methods

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

This is how it should look after following those steps:

<img width="1325" height="667" alt="Screenshot 2026-10-17 at 10 45 10 AM" src="https://github.com/user-attachments/assets/6baf78a0-0b1f-4db3-a88e-93865ac43166" />

After clicking "I acknowledge" & Save: 

<img width="1313" height="580" alt="Screenshot 2026-10-17 at 10 47 57 AM" src="https://github.com/user-attachments/assets/b2638e59-a501-45dd-8bbf-438c01c9925d" />

Make sure you document the configuration.

# Task 2: Test Microsoft Authenticator Registration & MFA Challenges
The goal here is to register a test user's authentication method and verify the MFA sign-in experience. You'll use one of the members in the IT security group and compare them to the other user if needed. 

# Step 1: Check the user's authentication methods
1. In Entra, navigate to Entra ID → Users → All users.
2. Select the user you wish to use for this step.
3. Open Authentication methods.
4. Review any methods already registered.

Do not record personal phone numbers, authentication QR codes, one-time codes, or recovery secrets in your project evidence.

# Step 2: Register Microsoft Authenticator
1. Open a separate private/incognito browser window.
2. Go to [My Sign-Ins Security Info](https://mysignins.microsoft.com/security-info?)
3. Sign in using the user's test-account credentials.
4. Select Add sign-in method.
5. Choose Authenticator app, if available.
6. Follow the on-screen setup process using Microsoft Authenticator on a device you control.
7. Complete the verification prompt.
8. Return to the Entra admin center and check the user's authentication methods again.

# Step 3: Verify an MFA Challenge
1. Open a new private browser session.
2. Sign in as the user you selected to a supported Microsoft sign-in destination in your lab.
3. Complete the additional authentication challenge if the policy requires it.
4. Record whether the sign-in succeeded, whether an MFA prompt appeared, and any error or policy result.
5. In the Entra admin center, navigate to Entra ID → Monitoring & health → Sign-in logs.
6. Filter for the user you registered and the time of your test.
7. Open the relevant event and inspect the Authentication Details and Conditional Access tabs, if available.

Do not assume a sign-in prompted for MFA just because the user has Authenticator registered. The sign-in logs and policy evaluation are the evidence that supports your conclusion.

This what the sign-in log should look like as an example in Authentication Details. 

<img width="1324" height="673" alt="Screenshot 2026-10-17 at 12 18 11 PM" src="https://github.com/user-attachments/assets/6a9ce43d-05d7-49c2-986e-30d0d213d13f" />

# Task 3: Create MFA & Administrative Conditional Access Policies
The goal here is to build policies that require MFA for a pilot group and evaluate MFA protection for administrative roles. 

Conditional Access generally requires Microsoft Entra ID P1 or a qualifying trial. If you do not have it, complete the policy design and document the limitation. Don't claim enforcement.

Let's set up some policies below!

Policy A: MFA for the IT Pilot Group Steps
1. Navigate to Entra ID → Conditional Access → Policies.
2. Select New policy.
3. Give the policy a name. I went with CA-Project2-MFA-IT-Pilot. You can use your own if you want.
4. Under Users or workload identities:
   - Include SG-IT-Operations.
   - Do not target all users for this lab.
5. Under Target resources, choose the supported resource selection appropriate for your tenant. If the interface offers All resources, use that only for the scoped pilot group after checking for policy conflicts.
6. Under Access controls → Grant, select Require multifactor authentication or the built-in MFA authentication strength, depending on the available interface.
7. Set Enable policy to Report-only.
8. Review the policy settings and select Create.
Report-only mode lets you evaluate how the policy would apply without enforcing its access controls. Microsoft recommends reviewing the impact before switching a policy on.

Policy B: MFA for Administrative Roles
This policy is intended to protect users with privileged directory roles.

1. Create another Conditional Access policy.
2. Give it a name as well. For this, I went with CA-Project2-MFA-Admin-Roles.
3. Under Users or workload identities, select Directory roles.
4. Select the privileged roles you intend to protect, using the role options shown in your tenant.
5. Under Target resources, choose the appropriate supported resource scope.
6. Under Grant, require MFA.
7. Set the policy to Report-only.
8. Create the policy and record its configuration.

Once you finish creating both policies, record both of the policies' purpose, users/roles, target resources, required control, mode, and expected result.

