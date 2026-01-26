# Data Leak Analysis

## Scenario
You work for an educational technology company that developed an application to help teachers automatically grade assignments. The application handles a wide range of data that it collects from academic institutions, instructors, parents, and students. Your team was alerted to a data leak of internal business plans on social media. An investigation by the team discovered that an employee accidentally shared those confidential documents with an external business partner. An audit into the leak is underway to determine how similar incidents can be avoided.

## 1. Incident Summary

A data leak occurred when internal confidential business plans were unintentionally shared externally. Investigation revealed the following:

- A sales manager shared access to an internal folder containing:

  - Confidential business plans

  - Customer analytics

  - Promotional content for an unreleased product

- The folder was shared with the sales team during a meeting, without revoking access afterward.

- A sales representative, forgetting the manager’s warning, attempted to share promotional materials with a business partner.

- Instead, they accidentally shared the internal folder link, giving the partner full access.

- The business partner then posted the link publicly on social media, assuming it was approved promotional content.

This event resulted in a public data leak of sensitive documents.

## 2. Control Evaluation – Least Privilege
**Control Identified:**

Least Privilege (NIST SP 800-53: AC-6)
Users should only be granted the minimum necessary access required to perform their duties.

Issues Identified

- Access to internal files was not limited; the sales team had broader access than necessary.

- The business partner was never supposed to have access to internal resources.

- No automated process existed to revoke access after the meeting.

- Employees relied on verbal instructions instead of enforced system controls.

What This Shows

The organization failed to enforce least privilege, allowing unauthorized sharing and exposure of sensitive data.

## 3. Review of NIST Control AC-6 (Least Privilege)

Based on NIST SP 800-53 AC-6:

**Control Definition**

Only the minimal access and authorization required to complete a task should be granted.

**Discussion**

To prevent misuse or accidental exposure, systems should enforce clear user roles, permissions, and access restrictions. Users must not operate with privileges beyond what is necessary.

**Control Enhancements**

- Restrict access based on role

- Automatically revoke access after task completion

- Maintain activity logs

- Regularly audit user privileges

These guidelines directly address the issues that caused the incident.

## 4. Root Cause Analysis

Based on the investigation:

**Primary cause:**

Excessive permissions were granted to the sales team.

**Secondary factors:**

- Lack of access expiration

- No automated access control

- Overreliance on employee memory (“don’t share this until approval”)

- No monitoring of shared links

- No distinction between internal-only documents and public-facing files

## 5. Recommendations

1. Implement Role-Based Access Controls (RBAC)

    Restrict sensitive folders so only authorized roles (e.g., product managers, executives) can view them.

2. Enforce Automatic Access Expiration

    Meeting-based or temporary permissions should automatically revoke after a set time.

3. Use “Internal Only” Access Settings

    Shared links should work only for internal employees with verified company accounts.

4. Conduct Regular Privilege Audits

    Audit user access rights quarterly to ensure least privilege is maintained.

5. Provide Visual Labels for Sensitive Files

    Use tags such as:

    - Internal Only

    - Confidential

    - Restricted Access

    This reduces accidental exposure.

6. Train Employees on Data Classification

    Include real scenarios demonstrating accidental leaks and proper sharing procedures.

7. Enable Monitoring & Alerts

    Set up alerts for:

    - External sharing of internal folders

    - Creation of public links

    - Downloads of confidential documents

## 6. Justification

These recommendations align directly with NIST SP 800-53 AC-6 and its enhancements:

- Restricting access based on role ensures only appropriate individuals can view sensitive data.

- Automatic revocation prevents accidental retention of access after meetings.

- Privilege audits reduce the chance of outdated or unnecessary permissions.

- Internal-only sharing blocks external exposure even if the wrong link is shared.

- Monitoring and logging allow quick detection and remediation of improper access.

By implementing these controls, the organization will significantly reduce the risk of accidental data exposure and strengthen its overall information privacy posture.

## 7. Summary

In this activity, I analyzed a data leak caused by misuse of access permissions and failure to enforce least privilege. I evaluated the incident using NIST SP 800-53 controls, identified gaps in access management, and recommended corrective actions such as RBAC, access expiration, privilege audits, and internal-only sharing controls. These improvements will help ensure the organization handles sensitive data securely and reduces the likelihood of similar incidents.

## References

<img width="539" height="354" alt="Screenshot 2026-01-26 at 11 09 22 PM" src="https://github.com/user-attachments/assets/4afb748d-7df8-45ec-9300-269d4e472887" />

<img width="539" height="529" alt="Screenshot 2026-01-26 at 11 09 43 PM" src="https://github.com/user-attachments/assets/d415e660-0bdf-4fba-8139-bac72c52c57b" />
