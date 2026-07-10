---
title: "Messaging & Event-Driven Systems"
---

- Queues, topics, pub/sub, work distribution, consumer groups, partitions, offsets, retention, ordering scope, and delivery guarantees.
- Kafka concepts: brokers, replication factor, ISR, partition key, consumer rebalances, commits, compaction, and schema registry.
- Design producers and consumers for duplicates, poison messages, slow consumers, backpressure, retries, DLQs, replay, monitoring, and safe reprocessing.
- Use the transactional outbox (and often inbox/deduplication) pattern to bridge a database update and event publication safely.
- Understand sagas: choreography versus orchestration, compensating actions, and the fact that compensation may be imperfect.
- Event sourcing and CQRS solve particular audit/read-model problems; account for versioning, replay cost, debugging, and operational complexity before adopting them.
