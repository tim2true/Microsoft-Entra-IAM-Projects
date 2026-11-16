# Project 4: Access Reviews & Identity Governance (IGA)

If you made it this far into the series of projects, we're going to continue using the same users and groups. I know, we can't let them go. They mean so much to us. 

Before we get started on this project, please verify that the users have the same properties and security group membership from the previous projects. From there, make sure your enterprise application assignments are direct or group-based. If you've already tested the SAML Toolkit application and everything seems to be fine, then review your sign-in logs and privileged roles. 

For sign-in logs, head to Identity → Monitoring & health → Sign-in logs. 
For privileged roles, head to Identity → Roles & admins → All roles.

# Task 1: Configure an Access Review in Entra
If you're licensed in Entra, you should be able to complete the steps below to do Access Reviews. 

First thing you'll do is sign into the Entra admin center.
From the sidebar, you will navigate from ID Governance → Access Reviews.
Select New access review, then select the option to review access to a resource.

<img width="817" height="414" alt="Screenshot 2026-11-15 at 8 33 13 PM" src="https://github.com/user-attachments/assets/ea128d21-993d-4c22-bc42-c09ceb60395d" />


The 2nd step from here, you'll have to choose Teams + Groups under the resource type.
Select the finance group for this exercise, then under user scope, select Everyone.

<img width="976" height="660" alt="Screenshot 2026-11-15 at 8 34 13 PM" src="https://github.com/user-attachments/assets/0b518e02-beb0-4af1-9b0c-dd47743e5cc4" />

You'll configure the Reviews settings by:

• Making sure your administration account is the reviewer [Selected group(s) or user(s)]

• Keeping Review type as single-stage

• Making duration under 7 days

• Turning Review recurrence into Quarterly

• Leave every other option default!

From there, make sure you give your access reviews a name for the finance group and do the same for every other group.

If you've followed along, your access reviews should be set up and now you should redirect to Microsoft's MyAccess link to perform the reviews of approve/deny. [My Access Microsoft Link](https://myaccess.microsoft.com/)

Make sure you're logged in as your same administrator account, or make an account and set the role for the account to be a Global Administrator to do the review.

Navigate under My Access → Access Reviews

Then you should be able to Approve/Deny according to your test users' group and role listing, but make sure you click Details.

If everything is fine, then you were able to do your first access review flawlessly!

If Microsoft accounted for any of the users in the groups wrongly, then go back into Entra and fix the issue within the groups and roles.
