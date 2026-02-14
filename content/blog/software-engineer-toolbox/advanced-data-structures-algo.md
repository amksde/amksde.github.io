---
title : "Advanced Data-Structures & Algorithms"
---

### Red-Black, AVL Trees
- used to maintain in memory sorted order in $O log(n)$
- used as memtables in log-structured databases

### B-Trees
- Fixed size blocks (e.g. 4KBs)
- A tree with n keys will have depth of O(log n)
- Most DBs can fit into a B-Tree that is 3 or 4 levels deep (a 4 level tree of 4KB pages with branching factor of 500 can store up-to 256TB data)
- B+ Tree optimizes the key storage

### Fractal Trees
- B-Tree variant that use some log-structured ideas to reduce disk seeks