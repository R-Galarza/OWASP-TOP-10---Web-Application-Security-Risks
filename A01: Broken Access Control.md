
# A01: Broken Access Control

## Overview

Broken Access Control occurs when an application fails to properly enforce restrictions on what authenticated or unauthenticated users are allowed to do.
When access checks are missing, poorly implemented, or only enforced on the client side, attackers can perform actions outside their intended permissions.

This vulnerability consistently ranks as one of the most critical risks because it often leads directly to data exposure, privilege escalation, or full account compromise.

---

## Attack Scenario

The application implements role-based access control (RBAC), where standard users and administrators have different privileges.

A regular authenticated user notices that restricted functionality is accessible by directly accessing backend endpoints, without proper authorization checks on the server side.

The attacker assumes:

* The user is authenticated but not privileged
* The application trusts client-side role validation
* Backend endpoints are not consistently protected

---

## Proof of Concept (PoC)

The attacker intercepts a legitimate request using Burp Suite and observes the following endpoint:

```http
GET /api/admin/users HTTP/1.1
Host: vulnerable-app.local
Cookie: session=USER_SESSION
```

Despite being authenticated as a standard user, the server responds with:

```json
{
  "users": [
    { "id": 1, "role": "admin" },
    { "id": 2, "role": "user" }
  ]
}
```

This confirms that the endpoint does not enforce proper authorization checks.

---

## Exploitation Walkthrough

1. Authenticate as a low-privileged user.
2. Intercept traffic and enumerate backend endpoints.
3. Access admin-restricted endpoints directly.
4. Modify requests to perform privileged actions such as:

   * Viewing other users’ data
   * Changing user roles
   * Deleting accounts

The lack of server-side authorization enables both horizontal and vertical privilege escalation.

---

## Impact

Successful exploitation may lead to:

* Unauthorized access to sensitive data
* Privilege escalation to administrator level
* Full account takeover
* Regulatory and compliance violations

In real-world environments, this vulnerability often results in complete system compromise.

---

## Root Cause Analysis

The core issue is the absence of server-side authorization enforcement.

Common contributing factors include:

* Trusting client-side role validation
* Inconsistent access checks across endpoints
* Missing centralized authorization logic

Adding authentication alone does not mitigate this vulnerability.

---

## Remediation Strategies

### Short-term fixes

* Enforce authorization checks on every request
* Deny access by default
* Validate user roles on the server side

### Long-term fixes

* Implement centralized access control mechanisms
* Use well-defined RBAC or ABAC models
* Apply the principle of least privilege

---

## Detection & Prevention

* Log and monitor unauthorized access attempts
* Use automated security testing to detect access control flaws
* Regularly review access rules and permissions

---

## References

* OWASP Top 10 – Broken Access Control
* [OWASP Top 10 – Web Application Security Risks](https://github.com/R-Galarza/OWASP-TOP-10---Web-Application-Security-Risks)

---

