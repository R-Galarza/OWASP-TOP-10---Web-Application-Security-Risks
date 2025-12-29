# A05: Injection

## Overview

Injection flaws occur when untrusted data is sent to an interpreter as part of a command or query.
SQL, NoSQL, OS command, and LDAP injections fall into this category.

---

## Attack Scenario

User input is directly concatenated into backend queries without proper validation.

---

## Proof of Concept (PoC)

```sql
SELECT * FROM users WHERE username = '$user' AND password = '$pass';
```

Payload:

```
' OR '1'='1
```

---

## Impact

- Data leakage
- Authentication bypass
- Remote code execution

---

## Root Cause Analysis

- Unsanitized user input
- Dynamic query construction
- Lack of parameterized queries

---

## Remediation Strategies

- Use prepared statements
- Apply input validation
- Use ORM frameworks securely

---

## References

- OWASP Top 10 – Injection

