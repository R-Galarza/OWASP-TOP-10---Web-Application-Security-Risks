# A03: Software Supply Chain Failures

## Overview

Software Supply Chain Failures occur when vulnerabilities are introduced through third-party libraries, dependencies, or external services.

---

## Attack Scenario

An application uses a vulnerable or compromised third-party component, which attackers exploit to gain access or execute code.

---

## Proof of Concept (PoC)

```text
Vulnerable dependency version detected in application stack
```

---

## Impact

- Remote code execution
- Compromise of trusted systems
- Loss of application integrity

---

## Root Cause Analysis

- Outdated or unverified dependencies
- Lack of dependency monitoring
- Blind trust in third-party components

---

## Remediation Strategies

- Maintain dependency inventories
- Monitor for known vulnerabilities
- Use trusted sources and integrity checks

---

## References
* [OWASP Top 10 – Software Supply Chain Failures](https://owasp.org/Top10/2025/A03_2025-Software_Supply_Chain_Failures/)

## Proof of Concept (PoC) Labs
* [Hack The Box Machine -]()
---


