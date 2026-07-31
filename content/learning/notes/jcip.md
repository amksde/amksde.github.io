---
title: "Java Concurrency In Practice - Notes"
date: "2006-10-21"
---
# Thread Safety 

- Sharing Objects 
- Out of thin air safety 
- Volatile variables 
- How they differ from synchronized 
- When to use vs when not to use?
- Locking vs Volatile for visibility and atomicity
- Publishing and escape
- Escaped variables 
- Safe Object Construction and escaping `this` reference 
- Thread confinement – local variables, stack confinement, and ThreadLocal<> 

# Immutability 

- Final field 
- Using volatile to publish immutable states 
- Weak atomicity using immutable objects 
- Collapsing invariants into an immutable holder
- Safe Publication 
- Safe publication idioms - static, final, or locks 

# Chapter 5: Building Blocks 

## Synchronized collections 

- Independent operations are thread safe, not compound ones
- Need client side locking
- Reduces scalability since they also block reads 
- Issue due to hidden iterators 

## Concurrent Collections 

- Provide iterators that don't throw `ConcurrentModificationException` - weakly consistent, not fail-fast
- Some Implementations
  - Map -> ConcurrentHashMap, List -> CopyOnWriteArrayList (read heavy) 
  - Queues -> ConcurrentLinkedQueue, PriorityQueue (not concurrent) 
  - BlockingQueue -> retrieval and insertion block until possible 
  - ConcurrentSkipListMap, ConcurrentSkipListSet for sortedMap and sortedSet 
- ConcurrentHashMap does not allow locking for exclusive access like Map and synchronized maps
- Blocking queues solve the producer-consumer problem - Bounded queues are a powerful resource management tool for building reliable applications: they make your program more robust to overload by throttling activities that threaten to produce more work than can be handled.
- 
 
