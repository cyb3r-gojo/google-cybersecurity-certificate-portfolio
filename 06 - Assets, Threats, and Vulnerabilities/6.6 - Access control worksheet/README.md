# Improve authentication, authorization, and accounting for a small business
This repository documents a security investigation into an unauthorized payroll transaction attempt at a growing business. As the company’s first cybersecurity professional, the task was to review event logs, identify the source of the incident, analyze access-control weaknesses, and recommend mitigation strategies to prevent recurrence.
## Scenario

You’re the first cybersecurity professional hired by a growing business.

Recently, a deposit was made from the business to an unknown bank account. The finance manager says they didn’t make a mistake. Fortunately, they were able to stop the payment. The owner has asked you to investigate what happened to prevent any future incidents.

To do this, you’ll need to do some accounting on the incident to better understand what happened. First, you will review the access log of the incident. Next, you will take notes that can help you identify a possible threat actor. Then, you will spot issues with the access controls that were exploited by the user. Finally, you will recommend mitigations that can improve the business' access controls and reduce the likelihood that this incident reoccurs.

## Notes From Event Log Review

Event logs in the Accounting-exercise.xlsx provided essential details for the investigation:

1. Who caused the incident?
   The action was executed using the Legal\Administrator account.

2. When did it occur?
   The unauthorized transfer occurred on 10/03/2023 at 8:29:57 AM.

3. What device was used?
  The event originated from device Up2-NoGud with IP address 152.207.255.255.

<img width="240" height="242" alt="Screenshot 2026-01-27 at 6 12 34 PM" src="https://github.com/user-attachments/assets/073197e8-f844-4a12-b660-9e170d591b4d" />


## Identified Access-Control Issues

Correlation between the Event Log and the Employee Directory exposed significant access-control failures:

1. What level of access did the user have?
   The user operated under an administrator-level account, granting full system privileges.

2. Should their account be active?
   No. The associated device and IP belong to a contractor who left the company in 2019, yet their account remained active for years.

Additional Issues:

- Shared or overly broad administrator access violated least-privilege principles.

- Dormant and unmonitored accounts created opportunities for misuse and unauthorized system activity.

<img width="1075" height="235" alt="Screenshot 2026-01-27 at 6 13 17 PM" src="https://github.com/user-attachments/assets/46977f4d-65c9-4e5e-af03-2fbeb39a2837" />


## Recommendations (Technical, Operational, and Managerial Controls)

**Technical Control** – Enforce Least-Privilege Access

- Remove shared administrator accounts.

- Assign user-specific credentials.

- Enforce multi-factor authentication for privileged roles.

- Restrict admin rights to only those who require them.

**Managerial Control** – Enforce Mandatory Account Deactivation Procedures

- All employee and contractor accounts must be disabled immediately upon departure.

- HR and IT must coordinate offboarding to ensure privilege removal.

**Operational Control** – Conduct Regular Access Audits

- Quarterly review of all user permissions.

- Identify inactive, stale, or escalated accounts and remove unnecessary rights.

These layered controls strengthen the business’s security posture and directly address the vulnerabilities exploited in the incident.

## Conclusion

This investigation demonstrates the ability to:

- Analyze and interpret event logs

- Identify misuse of administrative privileges

- Correlate data across multiple sources (event logs + employee directory)

- Apply least-privilege and access-governance principles

- Recommend actionable managerial, operational, and technical controls
