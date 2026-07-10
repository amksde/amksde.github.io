---
title: "Application Security"
---

- Threat model meaningful changes: assets, trust boundaries, attackers, abuse cases, mitigations, and residual risk.
- Authentication versus authorization; least privilege, RBAC/ABAC, tenant isolation, service identity, access reviews, and audit trails.
- OAuth 2.0/OIDC flows, sessions/cookies, JWT validation and rotation, password hashing with Argon2/bcrypt/scrypt, MFA, and account recovery.
- OWASP risks: injection, broken access control, SSRF, XSS, CSRF, insecure deserialization, path traversal, uploads, security misconfiguration, and vulnerable dependencies.
- Validate inputs at boundaries, encode outputs by context, use parameterized queries, set resource limits, and return safe errors.
- Store and rotate secrets using a secrets manager; scan code/builds/images, maintain an SBOM, sign/verify artifacts, and patch dependencies promptly.
