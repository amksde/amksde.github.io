---
title: "Advanced Data Structures & Algorithms"
---

These are especially useful for understanding databases, search engines, caches,
and high-scale systems.

- Balanced search trees: AVL and red-black trees maintain sorted in-memory data in `O(log n)` operations.
- B-trees and B+ trees: page-oriented, high-fan-out indexes that minimize storage reads; common in relational databases.
- LSM trees: writes first land in a memtable and immutable sorted files are compacted later; understand write amplification and compaction.
- Tries, radix trees, suffix structures, and finite-state machines for prefixes, routing, dictionaries, and text.
- Bloom/cuckoo filters and HyperLogLog: probabilistic structures that trade a bounded error for large memory savings.
- Skip lists and concurrent ordered maps.
- Consistent/rendezvous hashing, Merkle trees, vector clocks, and CRDT concepts for distributed data.
- Interval trees, segment/Fenwick trees, R-trees, and spatial indexes for range and geo queries.
- External-memory and streaming algorithms when data exceeds RAM.
