---
title : "Key Value Stores"
---
- Some datasets are simpler, fit into RAM, don't require disk. 
- Cache is also implemented using these
- KV stores are not faster because they serve data from memory. Even disk-based storage engines may never read from disk if enough memory is there. Real speed comes from avoiding the overhead of encoding in memory data structures in a disk-writable format
- KV Stores also offer some data-structures that are difficult to implement with disk - such as sets, priority queues, etc.
- 

1. Memcached
2. Redis
3. VoltDB
4. MemSQL
5. Oracle TimesTen
6. RAMCloud
7. Couchbase