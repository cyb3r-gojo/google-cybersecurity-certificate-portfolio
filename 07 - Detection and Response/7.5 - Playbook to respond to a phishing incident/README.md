# Phishing Alert Investigation – SOC Analyst Case Study

This repository documents a complete, end-to-end SOC Level-1 phishing alert investigation at a financial services company. The workflow follows the organization’s Phishing Incident Response Playbook and incorporates email analysis, malware verification, VirusTotal investigation, and final alert escalation.

## Scenario Summary

A financial services employee received a suspicious email containing a password-protected attachment. After downloading and opening the file using the provided password, a malicious payload executed on the workstation. Unauthorized executables were created, and the company’s intrusion detection system issued an alert.

The SOC’s job was to investigate the alert, confirm whether the attachment was malicious, and determine whether escalation was required.

## Investigation Steps (Playbook-Aligned)

<img width="327" height="613" alt="Screenshot 2026-01-30 at 12 28 40 AM" src="https://github.com/user-attachments/assets/8ee082ba-fc06-46aa-9c84-63ca7120c4df" />

#### 1. Alert Received

Alert ID: A-2703

Alert Type: SERVER-MAIL — Phishing attempt / possible malware download

Severity: Medium

The alert involved a suspicious attachment: ```bfsvc.exe```

#### 2. Evaluate the Alert (Playbook Step 2)

A full review of sender details, message content, and attachment behavior was performed:

**Sender Analysis**

- Sender name: Def Communications

- Claimed author inside email: Clyde West

- Actual sender address: 76tguyhh6tgftrt7tg.su

- Sender IP: 114.114.114.114

➡ Strong inconsistencies indicate spoofing and phishing.

**Email Body Indicators**

- Grammatical errors and unnatural sentence structure

- Suspicious mention of a role (“Infrastructure Egnieer role”)

- Claims of a job application, but mismatched naming

- Password provided in the body — common malware tactic

**Attachment Behavior**

- Attachment: bfsvc.exe (masquerading as a resume)

- Password-protected file → social engineering to bypass scanners

- File was downloaded and executed by the employee

#### 3. Malware Verification (VirusTotal)

The attachment's SHA-256 hash:

```54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b```

VirusTotal results showed:

- High vendor detection ratio (majority flagged as malicious)

- Negative community score

- Detection names consistent with Trojan / Downloader / Dropper malware

- Behavior analysis showed dropped executables, PowerShell execution, and attempted C2 activity

➡ File confirmed malicious.

#### 4. The 5 W’s (Journal Entry)

**Who:** A malicious actor sending phishing emails
**What:** Password-protected malicious attachment executed by employee
**When:** 1:11 p.m. email → 1:13 download → 1:15 malware execution → 1:20 IDS alert
**Where: **Employee workstation on the internal network
**Why:** Social engineering to coerce execution of malware and bypass detection

### Escalation Decision

- Based on the playbook's criteria:

    - The email contained an attachment
    - The attachment was confirmed malicious
    - Malware executed and created unauthorized files
    - The email sender was spoofed
    - Alert severity was Medium, qualifying for escalation

➡ The alert must be escalated.

## Final Alert Ticket (Completed)

Status: Escalated

### Ticket Comments Summary

- Employee downloaded and executed a malicious file from a phishing email.

- Sender details were clearly spoofed (mismatched names, suspicious domain).

- The file hash had been previously verified as malicious.

- Email body contained grammatical errors and a deceptive password-protected attachment.

- IDS detected execution of unauthorized files.

### Reasons for Escalation

- Confirmed malicious file hash and behavior.

- Clear phishing indicators (spoofing, grammar errors, password-protected attachment).

- Malicious payload executed, creating unauthorized files on the workstation.


## Key Learning Outcomes

This case study demonstrates how SOC analysts:

- Apply phishing detection playbooks

- Analyze suspicious email content and sender metadata

- Validate malware via hashing and VirusTotal

- Use evidence-based logic to escalate or close alerts

- Update SOC tickets with clear, actionable details

- Document findings using Incident Handler’s Journal best practices
