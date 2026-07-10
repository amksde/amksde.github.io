---
title: "System Design & Distributed Systems"
---

- Estimate traffic, storage, bandwidth, latency, availability, and cost before choosing components. State assumptions and bottlenecks.
- Understand horizontal/vertical scaling, load balancing, connection limits, caching, replication, partitioning/sharding, and data locality.
- Consistency: linearizability, serializability, eventual consistency, read-your-writes, quorum reads/writes, CAP trade-offs, and conflict resolution.
- Time and failure: clock skew, NTP, timeouts, partial failure, retries with jitter, exponential backoff, circuit breakers, bulkheads, backpressure, and load shedding.
- Delivery semantics: at-most-once, at-least-once, effectively-once; duplicates are normal, so build idempotent handlers.
- Consensus and coordination: leader election, leases, fencing tokens, distributed locks, ZooKeeper/etcd concepts, and why exactly-once distributed transactions are rarely free.
- Design for operability: bounded resources, overload behavior, observability, data repair, backup/recovery, migrations, multi-region trade-offs, and a tested rollback path.
