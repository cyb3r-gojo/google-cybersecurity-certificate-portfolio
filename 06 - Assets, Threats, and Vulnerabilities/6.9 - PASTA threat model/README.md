# PASTA Threat Model – Sneaker Marketplace Mobile App

This repository documents a complete PASTA (Process for Attack Simulation and Threat Analysis) threat model for a new sneaker marketplace mobile app. The model assesses business goals, technical architecture, threats, vulnerabilities, and recommended security controls for the application prior to launch.
## Scenario  
You’re part of the growing security team at a company for sneaker enthusiasts and collectors. The business is preparing to launch a mobile app that makes it easy for their customers to buy and sell shoes. 

You are performing a threat model of the application using the PASTA framework. You will go through each of the seven stages of the framework to identify security requirements for the new sneaker company app.



## I. Business & Security Objectives

The app must allow users to create accounts, log in securely, manage profiles, message sellers, and rate sellers. It must also support fast and reliable payment processing with multiple payment options while meeting compliance and financial regulations. Data privacy is essential, and the app must protect user information to maintain trust and legal compliance.

## II. Technical Scope

Technologies in use: API, PKI (AES + RSA), SHA-256, SQL

I prioritized evaluating the API first because it is the primary interface between the app and backend systems, making it highly exposed to attacker interaction. A vulnerable API could allow unauthorized access, data exposure, or manipulation. Issues such as improper authentication or lack of input validation create severe risks, including SQL injection and data leakage.

## III. Application Decomposition

<img width="1075" height="510" alt="Screenshot 2026-01-27 at 9 20 56 PM" src="https://github.com/user-attachments/assets/ce109ba2-49ff-4fbd-82d4-3f8ccc231409" />

**Data Flow Summary:**

1. User searches for sneakers in the app.

2. Search request is sent to the backend API.

3. API queries the SQL database for current inventory.

4. Database sends results back through the API to the user.

**Security Considerations:**

- API must sanitize user input before sending SQL queries.

- PKI (AES + RSA) must protect data in transit.

- SHA-256 must be used to hash sensitive data such as passwords.

- SQL queries must be protected using prepared statements.

## IV. Threat Analysis

**External Threat – SQL Injection Attacks:**
An attacker may exploit insufficient API input validation to inject malicious SQL queries and gain access to user data or sneaker listings.

**Internal Threat – Credential Misuse or Insider Data Theft:**
A malicious or careless employee with legitimate access may attempt to view, modify, or leak sensitive customer information.

## V. Vulnerability Analysis

**Improper Input Validation in API:**
If user input is not validated or sanitized, attackers could exploit this to perform SQL injection.

**Weak or Misconfigured Authentication Controls:**
If passwords are not properly hashed (SHA-256), or if MFA is absent, attackers may gain unauthorized access via brute-force, credential stuffing, or stolen credentials.

## VI. Attack Modeling

An attack tree diagram was analyzed to map threats and vulnerabilities to likely attack paths.
<img width="1075" height="510" alt="Screenshot 2026-01-27 at 9 23 26 PM" src="https://github.com/user-attachments/assets/0493ec95-143d-4798-9844-3075d9b5153f" />

**Mapped Findings:**

- SQL Injection aligns with the “lack of prepared statements” branch.

- Weak Credentials / Session Hijacking aligns with the “weak login credentials” and “session hijacking” branches.

These findings confirm the attacker's potential paths to compromise user accounts or backend systems.

## VII. Risk Analysis & Recommended Controls

Four controls that reduce the likelihood and impact of attacks:

**1. Strong API Input Validation + Prepared Statements**
    Prevents SQL injection and ensures safe database interactions.

**2. Multi-Factor Authentication (MFA)**
    Reduces the effectiveness of stolen or weak credentials.

**3. End-to-End Encryption Using PKI (AES + RSA)**
    Protects sensitive user and payment data from interception.

**4. Role-Based Access Control (RBAC)**
    Limits insider threats by granting users only the minimum permissions necessary.

## Conclusion

This PASTA threat model provides a structured evaluation of the sneaker marketplace mobile app’s security posture. By reviewing business objectives, architectural components, threats, vulnerabilities, and mitigation controls, this assessment highlights the critical areas requiring security hardening prior to app launch. Implementing the recommended controls will reduce risk, enhance customer trust, and help ensure the secure handling of user and payment data.
