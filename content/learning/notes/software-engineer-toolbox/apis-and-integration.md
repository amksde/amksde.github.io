---
title: "APIs & Integration"
---

- Model resources and workflows around users' needs; make contracts consistent, explicit, documented, and observable.
- HTTP: correct method/status use, validation errors, pagination (cursor versus offset), filtering, sorting, partial updates, content negotiation, caching, and rate-limit headers.
- Make unsafe operations idempotent with idempotency keys; define timeout, retry, duplication, and ordering behavior.
- Version deliberately. Prefer additive changes, tolerant readers, deprecation windows, and compatibility tests over frequent breaking versions.
- Know REST, GraphQL, gRPC, WebSockets, SSE, polling, and webhooks; select by latency, coupling, streaming, client, and operational needs.
- Secure integrations with scoped credentials, OAuth 2.0/OIDC, mTLS where appropriate, signature verification, replay protection, secret rotation, and auditability.
- Publish OpenAPI/AsyncAPI or protobuf schemas; use consumer-driven contract tests and sandbox/mock environments.
