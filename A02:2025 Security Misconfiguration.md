# A02: Security Misconfiguration

## Overview

Security Misconfiguration happens when systems are deployed with insecure default settings, unnecessary services enabled, or sensitive components exposed.

---

## Attack Scenario

An attacker discovers exposed admin panels, debug modes, or internal services due to improper configuration.

---

## Proof of Concept (PoC)

```text
http://risk-admin.vulnerable-app.local
```

---

## Impact

- Information disclosure
- Increased attack surface
- Facilitation of chained attacks

---

## Root Cause Analysis

- Default configurations left unchanged
- Unnecessary features enabled
- Lack of hardening procedures

---

## Remediation Strategies

- Apply secure configuration baselines
- Disable unused services and features
- Regularly audit configurations

---

## References

- OWASP Top 10 – Security Misconfiguration
