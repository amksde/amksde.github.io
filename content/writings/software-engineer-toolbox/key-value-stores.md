---
title: "Key-Value Stores & Caching"
---

- Key-value stores optimize simple access patterns and often offer useful in-memory structures such as sets, sorted sets, queues, streams, and counters.
- A cache is not automatically fast: hit rate, serialization, network hops, eviction, memory pressure, and invalidation determine the outcome.
- Know cache-aside, read-through, write-through, write-behind, TTL, eviction policies, negative caching, and cache warming.
- Prevent stampedes with request coalescing/single-flight, jittered TTLs, stale-while-revalidate, and bounded fallback behavior.
- Do not treat a cache as the source of truth unless its durability and consistency model truly fit the requirement. Design for cache loss and stale data.
- Redis/Memcached are common cache choices. Learn Redis persistence/replication, cluster/slot behavior, memory eviction, and the limits of distributed locks.
