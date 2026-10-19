# Threat Scenarios – Secure Attendance & Workforce Management System

## Overview

This document describes realistic threat scenarios identified during the threat modelling exercise of the Attendance & Workforce Management System.

The scenarios focus on risks affecting employee attendance records, workforce data, authentication services, APIs, databases, and administrative functions.

---

# Scenario 1 – SQL Injection Attack

## Description
An attacker discovers that a legacy API endpoint accepts unsanitized user input.

The attacker injects malicious SQL statements through a search field.

## Attack Path

1. Attacker accesses attendance search page
2. Malicious SQL payload submitted
3. Application fails to validate input
4. Query executed against database
5. Sensitive data exposed

## Impact

- Employee records exposed
- Attendance history modified
- Database corruption

## Risk Rating

**Critical**

## Recommended Controls

- Parameterized SQL queries
- Input validation
- Stored procedures
- Web Application Firewall (WAF)

---

# Scenario 2 – Compromised HR Account

## Description

An attacker obtains HR credentials through phishing.

The account is used to access workforce reports and employee records.

## Attack Path

1. Malicious phishing email sent
2. HR user enters credentials
3. Attacker logs into HR Portal
4. Sensitive information accessed

## Impact

- Personal information disclosure
- Payroll information exposure
- Regulatory compliance violations

## Risk Rating

**Critical**

## Recommended Controls

- Multi-Factor Authentication
- Security awareness training
- Account monitoring
- Session timeout enforcement

---

# Scenario 3 – Attendance Device Spoofing

## Description

An attacker imitates a legitimate attendance device and submits fraudulent attendance records.

## Attack Path

1. Spoofed device created
2. Fake requests sent to Attendance API
3. System accepts unauthenticated device traffic
4. False attendance records stored

## Impact

- Invalid attendance entries
- Payroll inaccuracies
- Loss of data integrity

## Risk Rating

**High**

## Recommended Controls

- Device certificates
- Mutual TLS
- Device registration process
- API authentication keys

---

# Scenario 4 – Privilege Escalation

## Description

An employee manipulates application parameters to gain HR privileges.

## Attack Path

1. Employee logs into portal
2. Hidden administrative URL discovered
3. Broken access control exploited
4. Administrative functions accessed

## Impact

- Unauthorized record changes
- Security control bypass
- Compliance violations

## Risk Rating

**Critical**

## Recommended Controls

- Role-Based Access Control (RBAC)
- Server-side authorization
- Periodic privilege reviews
- Security testing

---

# Scenario 5 – Insider Attendance Manipulation

## Description

A privileged user modifies attendance records without authorization.

## Attack Path

1. HR account access obtained
2. Attendance records edited
3. Audit logs disabled or modified

## Impact

- Payroll fraud
- Compliance issues
- Reduced trust in system data

## Risk Rating

**High**

## Recommended Controls

- Segregation of duties
- Immutable audit logs
- Behaviour monitoring
- Change approval workflow

---

# Scenario 6 – Session Hijacking

## Description

An attacker steals an active user session through insecure session management.

## Attack Path

1. Session token intercepted
2. Token reused by attacker
3. User account impersonated

## Impact

- Unauthorized access
- Data exposure
- Account takeover

## Risk Rating

**High**

## Recommended Controls

- Secure cookies
- Short token lifetime
- Automatic logout
- HTTPS/TLS enforcement

---

# Scenario 7 – Denial of Service Attack

## Description

An attacker floods Attendance APIs with excessive requests.

## Attack Path

1. Automated scripts send requests
2. API resources exhausted
3. Application performance degrades

## Impact

- Service outage
- Missed attendance submissions
- Business disruption

## Risk Rating

**High**

## Recommended Controls

- API rate limiting
- Traffic filtering
- Load balancing
- DDoS protection

---

# Scenario 8 – Database Backup Exposure

## Description

A database backup file is stored in an insecure location.

## Attack Path

1. Backup discovered by attacker
2. Backup downloaded
3. Sensitive employee data exposed

## Impact

- Data breach
- Regulatory penalties
- Reputation damage

## Risk Rating

**Critical**

## Recommended Controls

- Backup encryption
- Secure storage
- Access monitoring
- Backup retention policy

---

# Risk Prioritization Summary

| Threat Scenario | Risk |
|----------------|------|
| SQL Injection | Critical |
| HR Account Compromise | Critical |
| Privilege Escalation | Critical |
| Database Backup Exposure | Critical |
| Attendance Device Spoofing | High |
| Insider Manipulation | High |
| Session Hijacking | High |
| Denial of Service | High |

---

# Top Security Recommendations

1. Implement Multi-Factor Authentication (MFA)
2. Enforce Role-Based Access Control (RBAC)
3. Encrypt sensitive employee data
4. Enable centralized audit logging
5. Conduct regular vulnerability assessments
6. Perform annual penetration testing
7. Implement API rate limiting
8. Monitor privileged account activity
9. Deploy SIEM monitoring
10. Establish an Incident Response Plan

---

## Conclusion

The Attendance and Workforce Management System contains multiple critical assets that require strong protection. The highest risks involve unauthorized access, SQL injection, privilege escalation, and sensitive data exposure. Applying the identified security controls will significantly reduce risk and improve the security posture of the platform.
