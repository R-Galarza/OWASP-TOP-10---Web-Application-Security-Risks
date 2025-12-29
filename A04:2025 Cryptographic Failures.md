
# A02: Cryptographic Failures

## Overview

Cryptographic Failures occur when applications fail to properly protect sensitive data through encryption.
This includes weak algorithms, improper key management, missing encryption, or incorrect implementation of cryptographic controls.

These failures often result in data exposure rather than direct system compromise, but the impact can be severe.

---

## Attack Scenario

The application stores sensitive user data such as passwords or tokens.

The attacker observes that:

- Data is transmitted over HTTP instead of HTTPS
- Sensitive fields are stored using weak hashing algorithms
- Encryption keys are hardcoded or reused

---

## Proof of Concept (PoC)

Passwords are stored as plain text in the database:

```sql
SELECT username, password FROM users;
```

Result:

```
admin | admin123
user  | password
```

---

## Impact

- Credential theft
- Sensitive data disclosure
- Compliance violations (GDPR, PCI-DSS)

---

## Root Cause Analysis

- Lack of encryption at rest or in transit
- Use of outdated cryptographic algorithms
- Poor key management

---

## Remediation Strategies

- Enforce HTTPS everywhere
- Use strong hashing (bcrypt, Argon2)
- Secure key storage and rotation

---

## References
[OWASP Top 10 – Cryptographic Failures](https://owasp.org/Top10/2025/A04_2025-Cryptographic_Failures/)

## Proof of Concept (PoC) Labs
* [Hack The Box Machine -]()
---
