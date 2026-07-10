---
title: "Encryption & Key Management"
---

Encoding changes representation; encryption protects confidentiality. Hashing is
one-way and is used for integrity or password verification.

- Use well-reviewed libraries and proven constructions. Do not implement cryptography yourself.
- Hash passwords with a password-hashing function such as Argon2id, bcrypt, or scrypt with unique salts and appropriate parameters.
- Use authenticated encryption (for example AES-GCM or ChaCha20-Poly1305) for sensitive data; encryption without integrity is usually insufficient.
- Understand public/private keys, certificates, signatures, TLS, certificate validation, mTLS, HMAC, and token signing/verification.
- Use envelope encryption and a managed KMS/HSM where possible. Separate data-encryption keys from key-encryption keys, rotate keys, and restrict access.
- Protect secrets in transit, at rest, in logs, in backups, and in developer workflows. Define expiration, rotation, revocation, and incident procedures.
