# Final Incident Handler’s Journal – Cybersecurity Case Study

This repository contains a complete Incident Handler’s Journal documenting multiple cybersecurity learning activities, investigations, and hands-on tool usage. The journal entries reflect real-world SOC analyst workflows, including packet capture, malware investigation, phishing analysis, and incident documentation aligned to the NIST Incident Response Lifecycle.\

## Overview

Throughout the learning modules, multiple incidents and cybersecurity tools were explored. This journal is structured into four dated entries, each demonstrating:

- Use of SOC and IR tools

- Documentation of incident investigations

- Application of the 5 W’s methodology

- Mapping to appropriate NIST Incident Response Lifecycle phases

- Analyst reflections and personal learning observations

## Journal Entry #1 – Ransomware Incident Investigation

Date: July 23, 2024
Entry #: 1

**Description**
This entry documents a ransomware attack on a healthcare company. The investigation spans two phases of the NIST Incident Response Lifecycle:

- **Detection and Analysis:** Initial signs of system lockouts and ransom notes led to confirming a ransomware intrusion.

- **Containment, Eradication, and Recovery:** Systems were shut down to contain the attack, and external organizations were contacted for assistance.

**Tools Used**
None (initial documentation phase)

**The 5 W’s**
- **Who:** Organized group of unethical hackers

- **What:** Ransomware incident encrypting critical systems

- **Where:** Healthcare company internal network

- **When:** Tuesday, 9:00 a.m.

- **Why:** Attackers used phishing emails to gain access and deploy ransomware for financial gain

**Additional Notes**
Should the organization pay the ransom?

What long-term controls can prevent recurrence?

## Journal Entry #2 – Wireshark Packet Analysis

Date: July 25, 2024
Entry #: 2

**Description**

This entry documents the analyst’s first experience analyzing packet capture data using Wireshark. The goal was to explore network traffic patterns and identify areas where malicious activity might occur.

**Tools Used**

Wireshark – A GUI-based network protocol analyzer used to capture and inspect network traffic.

**The 5 W’s**

Not applicable (tool-focused entry)

**Additional Notes**

The interface was initially overwhelming, but the tool proved valuable for understanding real-time network communication.

## Journal Entry #3 – Capturing Packets with tcpdump

Date: July 25, 2024
Entry #: 3

**Description**

This entry documents capturing live network traffic using tcpdump, a command-line network protocol analyzer. The activity focused on filtering, capturing, and interpreting packet data.

**Tools Used**

tcpdump – CLI-based packet capture tool used for deeper inspection of raw network traffic.

**The 5 W’s**

Not applicable (tool-focused entry)

**Additional Notes**

Using tcpdump was challenging due to command-line complexity, but successful capture reinforced the value of careful syntax and methodical troubleshooting.

## Journal Entry #4 – Investigating a Suspicious File Hash

Date: July 27, 2024
Entry #: 4

**Description**

This entry documents using VirusTotal to analyze a suspicious file hash discovered on an employee workstation. This activity falls under the Detection and Analysis phase of the NIST Incident Response Lifecycle. The analyst validated that the file was malicious and traced the threat to a phishing email.

**Tools Used**

VirusTotal – Used to verify the file hash and check multi-vendor malware detection.

**The 5 W’s**

- **Who:** Unknown malicious actor

- **What:** Malicious email attachment (SHA-256 hash: 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b)

- **Where:** Employee workstation at a financial services company

- **When:** Alert triggered at 1:20 p.m. by IDS

- **Why:** Employee downloaded and executed the malicious attachment

**Additional Notes**

Should security awareness training be improved to reduce susceptibility to phishing attacks?

## Reflections & Notes
**Most Challenging Activity**

The tcpdump activity was the most difficult due to the need for precise command-line syntax. Repeating the activity improved confidence and accuracy.

**How Understanding Evolved**

Incident detection and response became clearer throughout the course. The analyst gained understanding of IR lifecycle phases, tools, and the importance of structured processes.

**Favorite Tool or Concept**

Network traffic analysis was the most engaging. Using protocol analyzers like Wireshark provided real visibility into real-time network behavior and sparked deeper interest in the topic.

## Summary

This Incident Handler’s Journal demonstrates growth across four core areas:

- Documenting incidents thoroughly and professionally

- Using essential cybersecurity tools (Wireshark, tcpdump, VirusTotal)

- Applying operational frameworks like the NIST IR Lifecycle

- Reflecting on challenges and skill progression

This journal serves as a foundational record of hands-on SOC experience and incident response methodology.
