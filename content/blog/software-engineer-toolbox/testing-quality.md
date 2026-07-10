---
title: "Testing & Quality"
---

- Write fast, deterministic unit tests around domain logic; use integration tests for real boundaries such as SQL, broker, filesystem, and HTTP behavior.
- Test contracts between services, critical end-to-end journeys, migrations, authorization, concurrency, failure paths, and backwards compatibility.
- Use test containers/ephemeral environments where they increase confidence; keep fixtures small, representative, and free of production PII.
- Apply property-based, fuzz, mutation, load, soak, chaos, and security testing where the risk justifies it.
- Treat coverage as a signal, not a goal. A high percentage does not prove behavior, and brittle tests slow delivery.
- Pair tests with static analysis, formatting, linters, dependency/license vulnerability checks, code review, and clear definition of done.
