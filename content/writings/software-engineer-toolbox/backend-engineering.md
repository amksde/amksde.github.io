---
title: "Backend Engineering"
---

## Runtime and language fundamentals

- Learn the runtime model of the language you use: memory allocation and reclamation, stack/heap or ownership, type system, errors, modules/packages, I/O, and the standard library.
- Concurrency: threads, async tasks, channels/queues, locks, atomics, visibility, cancellation, deadlines, bounded worker pools, and avoiding shared mutable state.
- Diagnose leaks, contention, deadlocks, thread or task-pool starvation, unbounded queues, excess allocation, and blocking calls in asynchronous paths.
- Use the language's profiler, debugger, runtime metrics, heap/allocation tools, thread/task dumps, and flame graphs. Tune only after measurement.

## Framework and application fundamentals

- Dependency management, reproducible builds, dependency locking, artifact registries, static analysis, and vulnerability scanning.
- Application lifecycle, dependency injection, configuration, validation, error handling, health checks, graceful shutdown, and scheduled/background work.
- Request handling: routing, middleware, serialization, timeouts, connection pooling, streaming, resource cleanup, and context propagation.
- Data access: transactions, connection pools, batching, lazy loading/query amplification, optimistic/pessimistic locking, migrations, and when a lower-level data-access layer is clearer.

## Cross-language implementation choices

- Compare synchronous, asynchronous, reactive, actor, and coroutine models by the workload and operational complexity—not fashion.
- Understand when native compilation, a VM, garbage collection, or manual/ownership-based memory management affects startup, latency, throughput, and deployment.

# Backend Execution Patterns
- Process Vs Threads
- Multi-process model of NGINX/Postgres, Redis Backup Routine (COW), race conditions?
- Multi thread - race conditions
- 
