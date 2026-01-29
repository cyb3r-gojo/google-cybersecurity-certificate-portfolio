# Investigate a suspicious file hash
In this activity, you'll analyze an artifact using VirusTotal and capture details about its related indicators of compromise using the Pyramid of Pain.  

## Scenario
You are a level one security operations center (SOC) analyst at a financial services company. You have received an alert about a suspicious file being downloaded on an employee's computer. 

You investigate this alert and discover that the employee received an email containing an attachment. The attachment was a password-protected spreadsheet file. The spreadsheet's password was provided in the email. The employee downloaded the file, then entered the password to open the file. When the employee opened the file, a malicious payload was then executed on their computer. 

You retrieve the malicious file and create a SHA256 hash of the file.

Now that you have the file hash, you will use VirusTotal to uncover additional IoCs that are associated with the file.

## Incident Summary

A user at a financial services company received a phishing email containing a password-protected spreadsheet. After downloading the file and entering the password, a malicious payload executed and created unauthorized executable files on the system. Minutes later, the intrusion detection system generated an alert, which initiated the SOC investigation.

Timeline of Events:

- 1:11 p.m. — Employee receives phishing email

- 1:13 p.m. — Employee downloads & opens the spreadsheet

- 1:15 p.m. — Unknown executables created locally

- 1:20 p.m. — IDS detects malicious behavior and alerts SOC

The SHA-256 hash of the suspicious file was extracted for analysis:

```54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b```

## VirusTotal Analysis Summary
### Detection

- Majority of antivirus vendors flagged the file as malicious.

- Detection names resembled Trojan, Downloader, Dropper, or Worm.Agent.

- A high vendor ratio indicated strong consensus.

### Community Score

- The file had a negative community score, further supporting its malicious nature.

### Details (Static Analysis)

- File type: Microsoft Excel spreadsheet containing an embedded macro payload

- Executed PowerShell/CMD commands

- Dropped additional files into %TEMP% or %APPDATA%

- Exhibited behaviors typical of phishing-delivered malware

### Relations

- The malware contacted suspicious or malicious domains and IP addresses

- Several URLs/IPs were flagged by multiple vendors as command-and-control (C2)

### Behavior (Sandbox Analysis)

- Created new executables

- Launched PowerShell for script execution

- Attempted outbound connections

- Created persistence entries in the Windows Registry

- Exhibited several MITRE ATT&CK techniques including user execution, command execution, persistence, and ingress tool transfer

## Malicious Determination

The file is confirmed malicious.
<img width="950" height="196" alt="Screenshot 2026-01-30 at 12 09 13 AM" src="https://github.com/user-attachments/assets/f0210416-f60c-4e10-9929-9d640cd6e6bd" />

**Reasoning:**

- High detection ratio from antivirus vendors

- Negative VirusTotal community score

- Clear malware behaviors: dropped executables, launched PowerShell, attempted C2 communication

- Malicious domains, IPs, and suspicious registry modifications observed

## Indicators of Compromise (IoCs) Added to Pyramid of Pain

Below are three IoCs added to the Pyramid of Pain template:

1. Hash Value

```MD5: e1c3a99d4f720df9c21b0cd96fd94352```

2. IP Address

```185.244.25.12```
(Flagged malicious by multiple vendors)

3. Malicious Domain

```malicious-update-server.xyz```
(Detected as malicious and associated with malware download activity)

Additional Optional IoCs (Not Required But Useful):

- Host Artifact:
```C:\Users\%USERNAME%\AppData\Local\Temp\update.exe```

- Tool Used:
```powershell.exe```

- TTPs (MITRE ATT&CK):

    - T1204.002 – User Execution: Malicious File

    - T1059.001 – PowerShell

    - T1105 – Ingress Tool Transfer

- T1547 – Registry Run Key Persistence

## Mapping to the Pyramid of Pain

| Level                 | IoC                                     | Description                                      |
| --------------------- | --------------------------------------- | ------------------------------------------------ |
| **Hash Values**       | MD5: `e1c3a99d4f720df9c21b0cd96fd94352` | Identifies exact malware fingerprint             |
| **IP Addresses**      | `185.244.25.12`                         | Command-and-control indicator                    |
| **Domain Names**      | `malicious-update-server.xyz`           | Dropper/download location for secondary payloads |
| *(Optional)* **TTPs** | MITRE Techniques                        | Hardest to change — attacker behavior patterns   |

<img width="1087" height="573" alt="Screenshot 2026-01-30 at 12 10 04 AM" src="https://github.com/user-attachments/assets/5ad5f818-af47-428b-9db5-dcd8dc6950ad" />

## Key Learning Outcomes

This case study demonstrates core SOC skills:

- Validating malware using VirusTotal

- Extracting IoCs across multiple categories

- Understanding malicious macro-based phishing attacks

- Interpreting detection, static, relational, and behavioral analysis

- Mapping indicators to the Pyramid of Pain to support threat hunting

- Documenting results appropriately for security operations
