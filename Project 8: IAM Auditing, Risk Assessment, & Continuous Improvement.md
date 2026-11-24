# Project 8: IAM Auditing, Risk Assessment, & Continuous Improvement
The scenario within our fictitious company is that they're conducting an internal IAM security audit. Management wants to verify that employees have appropriate access, terminated contractors cannot access company resources, privileged permissions are controlled, and suspicious identity activity is investigated.

We'll be using the same security groups and identities for this project. 

The responsibilities in this project is to:

• Audit user accounts and group memberships

• Review identity sign-in and audit logs

• Verify onboarding, transfers, and offboarding controls

• Identity IAM security gaps

• Create a risk register and remediation plan

• Develop IAM security metrics and a management report

# Task 1: Establish the IAM Audit Scope

We'll be creating a folder for this project, but we'll create 9 different subfolders within that same folder. Give it a name. For the 9 subfolders, we'll be using them for the Audit Scope, User and Group Audit, Sign-in and Audit Logs.. Pretty much for every task that'll be under this project.

# Task 2: Conduct a User Account and Group Membership Audit
Step 1: Review user accounts
1. Open the Microsoft Entra admin center.
2. Navigate to Entra ID → Users → All users.
3. Review each in-scope test user.
4. Record the user display name or a redacted identifier, account enabled status, department, job title, user type, and relevant account properties.
5. Compare the current state with your expected-state baseline.
Do not export or publish unnecessary personal information.

Step 2: Review security group membership
1. Navigate to Entra ID → Groups → All groups.
2. Open each in-scope security group.
3. Review its membership type, owners, and members.
4. Compare actual members with the expected group membership documented in Task 1.
5. Look for users who have retained access after a department transfer or termination.

Step 3: Validate joiner, mover, and leaver scenarios
Use the lifecycle cases from your earlier projects:
- Joiner: Confirm the new user is enabled and receives only the expected role-based group access.
- Mover: Confirm the transferred user has the new department's access and no longer has obsolete access from the previous department.
- Leaver: Confirm the former user is disabled, sessions were revoked where applicable, and relevant group/application access was removed.
For a disabled leaver, do not re-enable the account to perform this check.

Step 4: Record the result
For each identity/group, record:
- Expected state.
- Actual state.
- Evidence source and capture date.
- Result: Pass, Finding, or Needs Validation.
- Explanation and recommended next step.
Use Needs Validation when you cannot obtain enough evidence. Do not mark a control Pass solely because no problem was noticed.

Expected evidence: User and Group Audit spreadsheet, redacted screenshots, and a list of confirmed findings or validation gaps.

Save in 02 - User and Group Audit.

# Task 3: Review Sign-in Activity and Authentication Controls
The purpose is to understand whether authentication settings align with your intended security requirements and to inspect available sign-in activity.

Step 1: Review authentication methods
1. Navigate to Entra ID → Authentication methods → Policies.
2. Record which methods are enabled and which users/groups they target.
3. Review the authentication methods registered for selected test users under Users → [test user] → Authentication methods, where available.
4. Distinguish tenant-wide method availability from an individual user's registration.
Do not record secrets, QR codes, phone numbers, or one-time passcodes.
Step 2: Review Conditional Access policies
1. Navigate to Entra ID → Conditional Access → Policies.
2. Record each relevant policy's name, users/groups or roles in scope, target resources, grant controls, exclusions, and policy state.
3. Identify whether the policy is Report-only, On, or Off.
4. Review the policy's expected impact and possible conflicts.
A Report-only policy evaluates how a policy would apply but does not enforce its access controls. Do not describe it as enforcing MFA or blocking access.

Conditional Access generally requires Microsoft Entra ID P1 or a qualifying trial. If you do not have the required license, document the intended policy design and licensing limitation rather than claiming it was enforced.

Step 3: Review sign-in logs
1. Navigate to Entra ID → Monitoring & health → Sign-in logs.
2. Set a clear date range and filter for your test identities.
3. Review the sign-in status, application/resource, timestamp, failure reason, authentication details, and Conditional Access results when available.
4. Investigate unusual failures, unfamiliar applications, unexpected locations, or activity inconsistent with the test scenario.
5. Record the event ID or another safe reference where available.
A failed sign-in is not automatically malicious. Explain what the event demonstrates and what additional context would be needed.

Step 4: Document the review

Create a worksheet with:
- Review period and filters.
- Policy configuration and enforcement state.
- Authentication method observations.
- Sampled sign-in events.
- Investigation notes and outcome.
- Limitations, including missing logs or unavailable licensing.
Expected evidence: Sign-in and Authentication Review spreadsheet and redacted policy/log screenshots.

Save in 03 - Sign-in and Authentication Review.

# Task 4: Review Directory Audit Logs and Lifecycle Evidence
This task focuses on administrative activity and whether identity changes can be traced to an actor, time, and business reason.
Step 1: Open directory audit logs
1. Navigate to Entra ID → Monitoring & health → Audit logs.
2. Set the review period.
3. Filter or search for user and group management activity relevant to your test cases.
4. Review events such as user creation, account updates, group membership changes, account disablement, and session revocation when those events are available.
The exact event names and available details may vary by portal version and licensing.

Step 2: Trace lifecycle events
For each joiner, mover, and leaver scenario, try to identify:
- The request or ticket reference.
- The user/account affected.
- The action performed.
- The actor who performed it.
- The timestamp.
- The before-and-after state.
- Evidence that the resulting access was verified.

Step 3: Record evidence gaps
If an event cannot be found, record the search period, filters, and result. Use Not Located, Not Available, or Not Applicable accurately. Do not invent an event or timestamp.

A missing audit event in your export is an evidence limitation. It does not automatically prove that the administrative action did not happen.

Expected evidence: Directory Audit Log Review worksheet and relevant redacted event details.

Save in 04 - Directory Audit Logs.

# Task 5: Review Access Governance, Enterprise Applications, and Privileged Access
The goal is to verify that access is approved, appropriate, periodically reviewed, and limited to the permissions required.
Step 1: Review enterprise application assignments
1. Navigate to Entra ID → Enterprise applications → All applications.
2. Open each in-scope application.
3. Review assigned users and groups.
4. Compare assignments with your access model.
5. Where possible, separately inspect the application's own user provisioning and role/permission configuration.
Remember: Entra application assignment and application-side authorization are not the same thing. An Entra assignment does not automatically prove that the user has been provisioned in the application or has the correct data permissions.

Step 2: Review access packages and access reviews
If your tenant has the required Identity Governance licensing:
1. Review access package catalogs, packages, resource roles, request policies, approvers, expiration settings, and assignments.
2. Review access review definitions, reviewers, decisions, completion state, and whether decisions were applied.
3. Confirm that the review population matches the intended users and groups.
If these features are unavailable, document the limitation and perform a manual access certification using your user/group baseline. Clearly label it as a manual review, not a native Entra Access Review.

Step 3: Review privileged role assignments
1. Navigate to Identity Governance → Privileged Identity Management → Microsoft Entra roles → Assignments, if available.
2. Review Active, Eligible, and Expired assignments.
3. Record the user, role, assignment type, start/end date, and approval or activation requirements where visible.
4. Also navigate to Entra ID → Roles & admins and inspect relevant role assignments. Not every standing role assignment is necessarily managed through PIM.
5. Compare each assignment with the user's job responsibilities and least-privilege requirements.
Pay particular attention to standing Global Administrator access. Do not remove or modify an administrator assignment without confirming that it is not required for tenant recovery or lab administration.

PIM generally requires Microsoft Entra ID P2 or Microsoft Entra ID Governance. If unavailable, create a manual privileged-role inventory and state that JIT activation was not tested.

Step 4: Record the result
Document confirmed access, approvals, review decisions, privileged assignments, and evidence limitations.

Expected evidence: Access Governance and Privileged Access Audit spreadsheet, application assignment screenshots, and review/role evidence where available.

Save in 05 - Governance and Privileged Access.

# Task 6: Build the IAM Risk Register
The purpose of the risk register is to capture security scenarios that could affect identity confidentiality, integrity, or availability.

Step 1: Identify potential risk scenarios
Use these as starting points. They are risk hypotheses, not automatic findings:

Risk ID	– Potential risk scenario –	Evidence to validate
IAM-01	A transferred user retains access from a former department.	Current group membership, approved transfer request, before/after access.
IAM-02	A former employee or contractor retains access.	Account status, group memberships, app assignments, session revocation.
IAM-03	MFA is not required for the intended user population.	Policy state, scope, exclusions, sign-in evaluation, licensing.
IAM-04	Conditional Access policy scope or exclusions leave identities unprotected.	Policy configuration, included/excluded users, roles, and resources.
IAM-05	Access reviews are incomplete or decisions are not applied.	Review definitions, decisions, completion records, resulting access.
IAM-06	Access package settings permit inappropriate requests or excessive access duration.	Eligibility, resources, resource roles, approvals, expiration, assignments.
IAM-07	Privileged access is excessive, standing, or insufficiently reviewed.	Active/eligible role inventory, justification, approvals, activation settings.
IAM-08	Sign-in or directory audit logs are incomplete or not reviewed.	Log categories, retention, review period, reviewer records, escalation.
IAM-09	Entra app assignment does not match application-side authorization.	Entra assignments, provisioning state, app roles, application permissions.
IAM-10	JML actions cannot be traced to an approved request and verified result.	Ticket, approver, actor, timestamp, audit event, before/after evidence.

Step 2: Rate each risk
Use a consistent scale. One example:
- Likelihood: 1 (Rare) to 5 (Almost Certain).
- Impact: 1 (Negligible) to 5 (Severe).
- Inherent risk score: Likelihood × Impact.
- Suggested bands: 1–4 Low; 5–9 Moderate; 10–16 High; 17–25 Critical.
Define your rating criteria before scoring. If you use a different risk method, document it.

Step 3: Separate risk from finding
Use these distinctions:
- Confirmed finding: Evidence demonstrates that a control requirement was not met.
- Potential risk / validation required: A plausible exposure exists, but evidence is not sufficient to confirm a control failure.
- Observation: A factual condition that may warrant attention but is not necessarily a failure.
- Not applicable: The control does not apply, with a documented reason.
Record the evidence supporting the rating and the reason for the conclusion.
Step 4: Save the register
Suggested columns:

Risk ID | Risk Scenario | Asset/Population | Control Objective | Evidence Reviewed | Validation Status | Likelihood | Impact | Inherent Score | Existing Controls | Recommended Treatment | Owner | Due Date | Residual Risk

Expected evidence: Completed IAM Risk Register.

Save in 06 - IAM Risk Register.
# Task 7: Develop an IAM Remediation and Improvement Plan
The goal is to define practical actions that address confirmed findings and improve assurance over potential risks.
Step 1: Convert confirmed findings into actions
For every confirmed finding, describe:
- What the evidence showed.
- Why it matters.
- The required corrective action.
- The person/role responsible.
- Target completion date.
- Evidence needed to close the action.
- Success criteria.

Step 2: Add preventive improvements where no findings were confirmed
If your review did not identify confirmed findings, you can still create a continuous-improvement plan. Label these items as Preventive, Validation, or Control Sustainment actions—not corrective actions for a confirmed failure.

Examples:
- Revalidate mover access after each department transfer.
- Periodically confirm disabled leaver accounts have no residual access.
- Review Conditional Access policy scope and exclusions.
- Retain access review decisions and evidence that decisions were applied.
- Review privileged role assignments on a defined schedule.
- Define log review ownership and escalation.
- Standardize JML evidence and ticket references.

Step 3: Prioritize and assign actions
Use Critical/High/Medium/Low or another documented priority model. Assign a realistic owner and due date. Do not mark an action complete until the evidence and success criteria are satisfied.

Expected evidence: IAM Remediation Plan with status, owner, due date, required evidence, and closure notes.

Save in 07 - Remediation Plan.
# Task 8: Define IAM Security Metrics
Metrics help management understand whether identity controls are operating consistently. Every metric must have a defined numerator, denominator, reporting period, and evidence source.
Suggested metrics
Metric  –  Example calculation	 –  Evidence source
Account review coverage –	Accounts reviewed ÷ accounts in scope × 100	Dated user inventory and review records
Leaver deprovisioning completion –	Leavers with all required access removed ÷ leavers in period × 100	Offboarding tickets, account state, group/app checks
Mover access accuracy	Transfers with old access removed and new access verified ÷ transfers reviewed × 100	Transfer tickets and before/after group membership
MFA enforcement coverage	In-scope users covered by an enforced MFA control ÷ total in-scope users × 100	Conditional Access policy state/scope and sign-in evidence
Access review completion	Reviews completed by due date ÷ reviews scheduled × 100	Access review records
Privileged access review coverage	Privileged assignments reviewed ÷ privileged assignments in scope × 100	Role inventory and reviewer sign-off
Audit log review timeliness	Required log reviews completed on time ÷ reviews scheduled × 100	Review log and escalation records
Remediation closure rate	Actions closed with evidence ÷ actions due in period × 100	Remediation tracker


Metric rules
- Define the reporting period (for example, calendar month or quarter).
- Define the population before calculating the percentage.
- Do not treat tenant-level authentication-method availability as proof of user MFA coverage.
- Do not count Report-only policies as enforced MFA coverage.
- Do not report planned actions as completed remediation.
- If no events occurred in the period, report 0 events or N/A as appropriate; do not automatically report 100%.
- Keep the source evidence so another reviewer can reproduce the calculation.
Expected evidence: IAM Security Metrics workbook with formulas, definitions, reporting period, source references, and evidence qualification.

Save in 08 - IAM Security Metrics.
# Task 9: Optional Advanced Analysis with Log Analytics and KQL
This task is optional and depends on having the required log ingestion, workspace configuration, and licensing.
Step 1: Confirm log availability
If you have configured Microsoft Entra diagnostic settings to send supported logs to a Log Analytics workspace, confirm that the relevant tables contain data before running queries.

Do not assume that logs are available in a workspace merely because you can open Log Analytics.
Step 2: Explore sign-in activity
Example query for a workspace using the SigninLogs table:
```
SigninLogs
| where TimeGenerated >= ago(7d)
| project TimeGenerated, UserPrincipalName, AppDisplayName,
          ResultType, ResultDescription, IPAddress
| order by TimeGenerated desc
```

Example query to summarize failed sign-ins:
```
SigninLogs
| where TimeGenerated >= ago(7d)
| where ResultType != "0"
| summarize FailedAttempts=count() by UserPrincipalName, ResultDescription
| order by FailedAttempts desc
```

Step 3: Explore directory audit activity
If the AuditLogs table is available:
```
AuditLogs
| where TimeGenerated >= ago(30d)
| project TimeGenerated, ActivityDisplayName, Result,
          InitiatedBy, TargetResources
| order by TimeGenerated desc
```
Table schemas and available fields can vary. Inspect the schema and adapt the query to your workspace. A query returning no rows does not prove that no activity occurred; verify ingestion, time range, permissions, and table availability.
Step 4: Document your analysis
Save the queries, query date range, workspace/table names (redacted if public), results, and limitations.

Expected evidence: KQL query file or screenshots and a brief analysis note.
# Task 10: Prepare the Final IAM Audit Management Report
This is the final deliverable. The report should communicate the assessment to a manager or security lead—not simply repeat every screenshot.

Step 1: Write the executive summary
Summarize:
- What was assessed.
- The overall conclusion.
- The most important confirmed findings or observations.
- The highest-priority risks.
- The actions management should approve.
Do not claim there were no risks simply because you found no confirmed findings.

Step 2: Summarize scope and methodology
Include the users/groups/apps/roles reviewed, audit period, sampling approach, procedures, evidence sources, and limitations.

Step 3: Present results by control area
Summarize:
- User accounts and group membership.
- Joiner, mover, and leaver controls.
- Sign-in activity and authentication.
- Directory audit logging.
- Enterprise application access.
- Access governance and privileged roles.
For each area, distinguish confirmed findings, observations, and items needing validation.

Step 4: Summarize risks and remediation
Include the most important risk register items and the status of remediation actions. Do not represent planned or proposed actions as completed.

Step 5: Present metrics carefully
Include the reporting period, numerator, denominator, formula, and evidence source for each metric. Label any metric that could not be independently validated.

Step 6: State limitations and conclusion
Document licensing limitations, unavailable logs, missing evidence, and any application-side controls you could not inspect. Conclude with the overall control posture supported by the evidence.

Step 7: Obtain review and sign-off
Include prepared-by, reviewer, approver, date, and comments fields. In a personal lab, these can be marked Self-review / simulated approval; do not imply an actual company management approval.

Expected evidence: Final IAM Audit Management Report saved in 09 - Final Management Report.
Project Completion Checklist
- [ ] Task 1: Audit scope and expected-state baseline documented.
- [ ] Task 2: User and group access reviewed against the baseline.
- [ ] Task 3: Authentication, Conditional Access, and sign-in activity reviewed.
- [ ] Task 4: Directory audit events and lifecycle evidence reviewed.
- [ ] Task 5: Application access, governance, and privileged roles reviewed.
- [ ] Task 6: Risk register completed with evidence-based validation status.
- [ ] Task 7: Remediation/improvement actions assigned and tracked.
- [ ] Task 8: IAM metrics defined with reproducible calculations.
- [ ] Task 9: Optional KQL analysis completed or marked not performed.
- [ ] Task 10: Final management report prepared and reviewed.
- [ ] All public screenshots and files redacted; no secrets or real personal data included.
What You Should Have at the End
Your Project 8 folder should contain:
1. Audit Scope document.
2. User and Group Audit workbook.
3. Sign-in and Authentication Review workbook.
4. Directory Audit Log Review workbook.
5. Access Governance and Privileged Access Audit workbook.
6. IAM Risk Register.
7. IAM Remediation Plan.
8. IAM Security Metrics workbook.
9. Final IAM Audit Management Report.
10. Optional KQL queries and analysis notes.
The deliverable should show how you defined the audit, collected evidence, evaluated identity controls, documented uncertainty, prioritized risk, and communicated recommendations. The quality of the audit depends on evidence and reasoning—not on producing a predetermined number of findings.
