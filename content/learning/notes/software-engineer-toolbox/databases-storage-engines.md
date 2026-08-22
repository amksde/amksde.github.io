---
title: "Databases & Storage Engines"
---

## Relational database fundamentals

- Model entities, relationships, constraints, keys, normalization/intentional denormalization, and tenant boundaries.
- SQL fluency: joins, aggregations, window functions, common table expressions, transactions, migrations, and parameterized queries.
- Indexes: composite/covering/partial indexes, selectivity, cardinality, index-only scans, write cost, and reading `EXPLAIN`/query plans.
- Transactions: ACID, isolation levels, MVCC, locks, deadlocks, optimistic/pessimistic concurrency, and safe retry boundaries.
- Operate safely: backups/PITR, restore drills, replication, failover, connection pooling, slow-query analysis, schema change rollout, and data repair.

## Storage-engine concepts

- Page cache, WAL, B/B+ trees, LSM trees, memtables, SSTables, compaction, bloom filters, checksums, and write/read amplification.
- Compare consistency, durability, query flexibility, latency, availability, operational burden, and cost before selecting a store.

## Databases worth understanding

- PostgreSQL and MySQL for transactional relational workloads; SQLite for embedded/local workloads.
- Redis for cache/data-structure use cases; Elasticsearch/OpenSearch for search (not as a primary source of truth by default).
- MongoDB/document stores, Cassandra/HBase/wide-column stores, and DynamoDB-style managed key-value stores for their specific access patterns.
- RocksDB/LevelDB/LMDB/Bitcask as embedded storage-engine concepts.
