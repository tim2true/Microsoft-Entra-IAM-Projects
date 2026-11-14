# Project 3: Enterprise Application and SSO
This project builds on Projects 1 and 2 by showing how an IAM analyst controls access to an enterprise application through Microsoft Entra ID, configures single sign-on, and investigates access failures.

You’ll reuse the same lab users and groups, and document the work.
In this project, you'll learn to: 

• Register or add a test enterprise application in Entra.

• Restrict application access to approved users or security groups.

• Configure SAML-based SSO for a supported test application.

• Test allowed and unassigned users.

• Inspect sign-in logs and troubleshoot common SSO configuration issues.

• Produce an application access matrix, configuration record, and troubleshooting report.

# Task 1: Add a Test Enterprise Application

From here, what you'll do is head to Entra Admin Center, then look for Enterprise Apps.

<img width="1721" height="957" alt="Screenshot 2026-10-31 at 8 24 27 AM" src="https://github.com/user-attachments/assets/36fa4455-b490-4cf1-922b-d48442fa8b16" />

Once you see this screen, click on New Application and search for Microsoft Entra SAML Toolkit.

<img width="1716" height="956" alt="Screenshot 2026-10-31 at 8 28 46 AM" src="https://github.com/user-attachments/assets/9aa31d5d-9cb3-4bfd-8e22-c29792d6d61a" />

The hyperlink under the title of the toolkit will help you along for clarification on the steps below.

Click on to it, then follow the workflow to add it to your tenant. After adding it, open the new application's overview page.

After reaching the overview page, get on over to the Properties page. 

Record the current values for:
- Enabled for users to sign in
- Assignment required
- Visible to users, if shown

Set Assignment required to Yes if the property is available and the application is dedicated to your lab. Confirm that sign-in is enabled, then select Save if you made changes.

It should look like this. 

<img width="1720" height="958" alt="Screenshot 2026-10-31 at 8 48 17 AM" src="https://github.com/user-attachments/assets/81966c5c-0a49-4f32-a9d1-a96399e9dd04" />

# Task 2: Restrict Application Access to an Approved Group

Let's get started by involving one of your security groups into this task. We can start off with the finance group.

Under the application's side menu, go down to where it says Users and Groups, then assign the finance group to the application.

Verify that a user you've created and assigned to that group in previous projects is in there. Confirm that the other members aren't included in it either. Same with the user that you've disabled in previous projects.

# Task 3: Configure SAML Single Sign-On

Going back into your application's side menu, search for where it should say Single Sign-on, and access it. After doing so, select your single sign-on method to be SAML.

Under the Set up Microsoft Entra SAML Toolkit step, record the information that is there.

<img width="817" height="208" alt="Screenshot 2026-10-31 at 9 11 07 AM" src="https://github.com/user-attachments/assets/2bc2eec3-6d9c-460d-96a1-c85012811b36" />

After recording the information, head back up to the first step in the SAML application set up and enter the values you've recorded from the step above and save it.

On the same configuration page, look where it says Attributions & Claims as step 2. Review the default claims, such as the unique user identifier and email-related claims.
Record which attribute the application expects to identify the user. Modify a claim if the test application's instructions require it and avoid adding unnecessary personal attributes to the SAML token.

After doing so, you'll go back into SAML certifications which is the step after Attributions and Claims. Record the certificate's status and expiration date. If the test application requires the certificate, download the appropriate certificate file and configure it in the application as instructed. Store any downloaded configuration artifacts securely; don't publish private keys or secrets.

<img width="710" height="367" alt="Screenshot 2026-10-31 at 9 40 22 AM" src="https://github.com/user-attachments/assets/94bea51f-c645-4f72-9de9-54e744c193b7" />


# Task 4: Test SSO with Assigned/Unassigned Users

For this task, you'll use a user that is already assigned to this SAML application by the finance group, a user that isn't assigned from the group, and the user that you disabled. 

When you go to click on Test this application, it'll bring up this screen. 

<img width="1439" height="811" alt="Screenshot 2026-11-13 at 6 40 22 PM" src="https://github.com/user-attachments/assets/35256247-1029-432c-8b15-0e29f7ac56c8" />

From here, if you have the Microsoft Entra tab that helps walk you through the setup for the Toolkit application, you should see the steps on how to fully setup and configure it for testing. 

But for those who haven't done so, I'll show off the steps below. 

Register and log in with the same username (email) that you're doing this project with. 

After doing so, look up at the first few tabs next to the Toolkit title, and you'll see SAML configuration. Navigate to the tab. 

Then you'll come across a screen that looks like this after you click on Create under SAML configuration!

<img width="1053" height="488" alt="Screenshot 2026-11-13 at 6 44 25 PM" src="https://github.com/user-attachments/assets/dd211838-050c-4fc6-8f56-6d7d331efefe" />

What you'll do from here is use the recorded data from your SAML toolkit configuration and enter it in the values above, then you'll click Create.

Go back into Entra and look into your SAML configuration set up. In basic SAML configuration, the new data that you've applied into your SAML configuration set up on the separate website, you'll go ahead and enter the data in their respective textboxes. From there, make sure you save and then you'll be able to finally test. 

Test a user that is assigned to your finance group, a user that isn't a part of your finance group, and a user that was disabled.

One user should be able to log in, one user should get a message saying that they aren't allowed to, and one user should get a message saying their sign-in is blocked because of account restrictions. 

There you have it, you enabled and set up SAML/SSO!
