---
title: "Performance & Capacity"
---

- Measure p50/p95/p99 latency, throughput, error rate, utilization, queue depth, allocation, GC pauses, and database query behavior.
- Use profiling and tracing before tuning. Benchmark with a realistic workload, warm-up, dataset, concurrency, and environment; avoid microbenchmark traps.
- Know queuing basics: as utilization approaches saturation, tail latency rises sharply. Bound queues and apply backpressure.
- Optimize common service paths: reduce allocation/copying, batch I/O, use connection pools correctly, avoid query amplification, index queries, and cache only with a sound invalidation strategy.
- Model capacity for peak and failure scenarios; define headroom, autoscaling signals, load-shedding policy, and cost limits.
