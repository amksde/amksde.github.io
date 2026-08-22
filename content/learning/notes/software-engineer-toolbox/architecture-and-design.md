---
title: "Architecture & Design"
---

- Start with functional and non-functional requirements: correctness, latency, availability, durability, security, cost, operability, and delivery constraints.
- Model the domain: ubiquitous language, bounded contexts, aggregates, invariants, state machines, and explicit ownership.
- Prefer a well-modularized monolith until independent deployment, scaling, ownership, or reliability needs justify service boundaries.
- Apply separation of concerns, dependency inversion, cohesion/coupling, clean/hexagonal architecture, and design patterns as tools—not ceremony.
- Design for change: stable interfaces, anti-corruption layers, strangler migrations, feature flags, expand/contract database migrations, and backwards compatibility.
- Write short ADRs and design documents that state context, options, decision, consequences, risks, rollout, observability, and rollback.
- Refactor continuously: improve names, remove duplication, contain side effects, pay down risky debt, and distinguish accidental from essential complexity.
