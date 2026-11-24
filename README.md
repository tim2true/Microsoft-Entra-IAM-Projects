# Microsoft Entra IAM Projects
A practical, step-by-step Microsoft Entra ID lab series covering the identity lifecycle, access administration, authentication, identity governance, privileged access, and IAM auditing.

This repository is designed for learners building hands-on IAM skills. Each project uses a fictional organization and test identities to walk through common identity-security scenarios—from onboarding and department transfers to access reviews, privileged role management, audit logging, risk assessment, and remediation planning.

The goal is to make IAM concepts practical and repeatable: understand the business request, configure or inspect the relevant Entra controls, validate the result, collect evidence, and document what the evidence actually proves.
Lab only: Use a dedicated test tenant and fictional identities. Never perform these exercises in a production tenant or publish passwords, MFA secrets, personal information, tenant identifiers, or unredacted security logs.

# What You'll Practice
- Identity lifecycle management: Joiner, mover, and leaver (JML) processes, account status, group membership, and access removal.
- Access control: Security groups, role-based access control (RBAC), least privilege, and access assignments.
- Authentication security: Authentication methods, MFA registration, Conditional Access policy design, and sign-in analysis.
- Enterprise application access: Application assignments, SAML single sign-on (SSO), and the distinction between directory assignment and application-side authorization.
- Identity governance: Access reviews, access packages, request/approval workflows, and access expiration.
- Privileged access management: Privileged role inventory, eligible assignments, just-in-time (JIT) activation, and administrative access review.
- IAM operations and assurance: Audit logs, evidence collection, risk registers, remediation plans, security metrics, and management reporting.

# Project Roadmap
[Project 1 — Identity Lifecycle and Access Provisioning](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%201%3A%20Identity%20Lifecycle%20and%20Access%20Provisioning.md) – Create fictional users and groups; practice onboarding, department transfers, and contractor offboarding.

[Project 2 — Microsoft Entra ID Access Control & Security](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%202%3A%20Microsoft%20Entra%20ID%20Access%20Control%20%26%20Security.md) – Review authentication methods, register MFA, configure Conditional Access policies, and inspect sign-in results.

[Project 3 — Enterprise Application Access & SSO](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%203%3A%20Enterprise%20Application%20Access%20%26%20SSO.md)	– Assign users to enterprise applications and explore SAML SSO configuration and troubleshooting.

[Project 4 — Access Reviews & Identity Governance (IGA)](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%204%3A%20Access%20Reviews%20%26%20Identity%20Governance%20(IGA).md) – Review group access, certify access, and document governance decisions.

[Project 5 — Self-Service Access Requests & RBAC](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%205%3A%20Self-Service%20Access%20Requests%20%26%20RBAC.md)	– Build access request scenarios with eligibility, approvals, resource roles, and expiration.

[Project 6 — Privileged Access Management with Microsoft Entra PIM](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%206%3A%20Privileged%20Access%20Management%20(PAM)%20with%20Microsoft%20Entra%20PIM.md)	– Inventory privileged roles and explore eligible assignments, JIT activation, and approval controls.

[Project 7 — PowerShell and Microsoft Graph Automation (On Hold)]()	– Optional automation extension; currently on hold.

[Project 8 — IAM Auditing, Risk Assessment, & Continuous Improvement](https://github.com/tim2true/Microsoft-Entra-IAM-Projects/blob/main/Project%208%3A%20IAM%20Auditing%2C%20Risk%20Assessment%2C%20%26%20Continuous%20Improvement.md)	– Audit identities and access, review logs, assess risks, define metrics, and prepare a management report.


# How to Use This Repository
1. Prepare a dedicated Entra lab tenant. Confirm you are not signed in to a production directory.
2. Create fictional test identities and security groups. Use a verified domain in your own tenant. The names in the guides are examples; substitute your own users, groups, departments, and applications.
3. Work through the projects in order. Later projects build on the identities and access model from earlier projects.
4. Follow the validation steps. Do not stop after changing a setting—verify the resulting account state, assignment, policy evaluation, or log event.
5. Save evidence as you go. Capture redacted screenshots, configuration notes, audit records, and project workbooks.
6. Document limitations honestly. Entra features may depend on licensing, tenant configuration, permissions, or log retention. If a feature is unavailable, document the intended design and the limitation rather than claiming it was configured or enforced.
7. Adapt the lab. Use the example scenarios as a starting point. Your own fictional user and group names should work as long as you keep a consistent expected-access baseline.
Recommended Lab Practices
- Use fictional identities and non-production data only.
- Keep a documented baseline of each user's department, job title, account status, group membership, app access, and privileged roles.
- Use least privilege; avoid assigning powerful roles unless a task requires a controlled test.
- Keep disabled former users disabled. Use a separate test identity if an enabled sign-in test is needed.
- Treat Report-only Conditional Access policies as evaluation-only, not enforcement.
- Separate confirmed findings from potential risks and evidence gaps.
- Never publish passwords, temporary access credentials, MFA codes, QR codes, recovery secrets, personal phone numbers, or unredacted identifiers.
- Check Microsoft licensing requirements before planning a feature-dependent task.
Disclaimer
This repository is an independent educational lab and is not affiliated with or endorsed by Microsoft. Microsoft Entra features, portal navigation, licensing, and available options may change over time. Always consult current Microsoft documentation and verify the options available in your own tenant.

The projects are for learning and portfolio demonstration. They do not constitute a formal security audit, compliance certification, or authorization to test systems you do not own or administer.
