# 6.2 - Risk Register

## Overview

This activity focuses on identifying assets, analyzing associated risks, and calculating risk priority using a structured risk register. Following cybersecurity best practices, each risk is evaluated based on likelihood, severity, and impact. The resulting risk scores help determine which risks require immediate attention and which are lower priority.

## Project Environment
The bank is located in a coastal area with low crime rates. Many people and systems handle the bank's
data—100 on-premise employees and 20 remote employees. The customer base of the bank includes
2,000 individual accounts and 200 commercial accounts. The bank's services are marketed by a
professional sports team and ten local businesses in the community. There are strict financial
regulations that require the bank to secure their data and funds, like having enough cash available
each day to meet Federal Reserve requirements.

### Risk Table

| **Asset**                | **Risk(s)**               | **Description**                                                               | **Likelihood** | **Severity** | **Priority** |
| ------------------------ | ------------------------- | ----------------------------------------------------------------------------- | -------------- | ------------ | ------------ |
| Funds                    | Business email compromise | An employee may be tricked into sharing confidential financial information.   | 2              | 2            | 4            |
| Customer Database        | Compromised user records  | Customer data may be poorly encrypted, increasing exposure in case of breach. | 2              | 3            | 6            |
| Financial Records Backup | Data leakage              | A backup database server may be publicly accessible due to misconfiguration.  | 3              | 3            | 9            |
| Physical Cash Safe       | Theft                     | The safe may be left unlocked, exposing funds to physical theft.              | 1              | 3            | 3            |
| Supply Chain             | Service disruption        | Delivery delays due to natural disasters affecting operations.                | 1              | 2            | 2            |

## Notes

Working with external vendors increases potential attack surfaces.

Physical theft risk is relatively low due to the organization’s location but still requires attention.

The highest-priority item in this register is the financial records leak with a risk score of 9, requiring immediate remediation.

Misconfigured systems, especially publicly accessible servers, represent severe cybersecurity threats.

## Definitions

These definitions follow the exemplar risk register:

**Asset:**
A resource that may be harmed, damaged, or stolen.

**Risk(s):**
Potential threats that could exploit vulnerabilities.

**Description:**
Explanation of the vulnerability that could lead to an incident.

**Likelihood (1–3):**
Probability that a vulnerability will be exploited.

1 = Low

2 = Moderate

3 = High

**Severity (1–3):**
Impact on the business if the threat occurs.

1 = Low

2 = Moderate

3 = High

**Priority (Risk Score):**v
Calculated by:
```
Likelihood × Severity
```
A high score means the risk should be addressed quickly.

## 📊 Sample Risk Matrix

This matrix is used to determine the risk score

| Likelihood \ Severity | **Low (1)** | **Moderate (2)** | **Catastrophic (3)** |
| --------------------- | ----------- | ---------------- | -------------------- |
| **Certain (3)**       | 3           | 6                | 9                    |
| **Likely (2)**        | 2           | 4                | 6                    |
| **Rare (1)**          | 1           | 2                | 3                    |

## Summary

In this activity, I analyzed assets, identified associated risks, and calculated risk priority levels using a standardized risk register. I evaluated each risk by examining likelihood, severity, and exposure. This process helps organizations decide which vulnerabilities require immediate remediation and which pose minimal risk. By completing this task, I demonstrated my ability to perform structured risk analysis, evaluate organizational assets, and apply cybersecurity risk-management frameworks.
