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
- **Blocking Queues**
  - Blocking queues solve the **producer-consumer problem** - Bounded queues are a powerful resource management tool for building reliable applications: they make your program more robust to overload by throttling activities that threaten to produce more work than can be handled.
  - BlockingQueue implementations -> LinkedBlockingQueue, ArrayBlockingQueue, PriorityBlockingQueue, SynchronousQueue
  - BlockingQueue for local programs is like Kafka for distributed systems. It helps divide breaking tasks into smaller components.
  - `Executor` task execution framework itself is based upon producer-consumer pattern, but does thread management as well
  - Serial Thread Confinement : Ownership transfer of mutable objects between producers and consumers
- We also have `Deque` and `BlockingDeque` - they extend the Queue class - implementations include `ArrayDeque` and `LinkedBlockingDeque` resp.
  - They used in the **work-stealing pattern**
  - Work stealing is well suited to problems in which consumers are also producers — when performing a unit of work is likely to result in the identification of more work.
  - Examples - web crawlers, graph based algorithms. Workers which identify new work place it at the end of their queue
  - See also, work-sharing pattern

## Blocking & Interruptible Methods
- Blocked threads are suspended & put into `BLOCKED`, `WAITING`, or `TIMED_WAITING`
- When a method can throw InterruptedException, it is telling you that it is a blocking method, and further that if it is interrupted, it will make an effort to stop blocking early
- Cannot throw an `InterruptedException` from a Runnable because Java's method overriding rules prohibit an overriding method from adding new checked exceptions to its signature
- Whenever you catch InterrupedException, either propagate it, or set the interrupt flag true in the current thread. Don't swallow it. Information about the interrupt must go upwards the call stack.
- `interrupt()` method does 2 things - set the interrupt flag, and if thread is blocked in an interruptible operation, wake it immediately.

## Synchronizers
- A synchronizer coordinates the flow of thread based on its state
- Examples - blocking queues, semaphores, barriers, latches, etc.
- **Latch**
  - `CountDownLatch` is a good latch implementation. Latches are used to block on dependencies or external events.
  - Examples are application bootstrap, microservice startup, async tasks, parallel file processing, external system startups, etc.
  - Modern alternatives are CompletableFuture, and structured concurrency since Java 21+
  - Starting gate and ending gate are two good use cases of latches as well
- **`FutureTask`** can be used to start execution of tasks whose results will be required later on.
- **Semaphore**
  - Counting semaphores are used to allocate and manage resource pools - such as database connection pools
  - A binary semaphore can be used as a mutex with nonreentrant locking semantics; whoever holds the sole permit holds the mutex
  - Try not to use semaphores as locks, use dedicated locking APIs, such as `ReentrantLock` lock. Semaphore's acquire is not re-entrant :(
- **Barriers**
  - Latches wait for events, barriers wait for threads
  - When a barrier is passed, all threads are released, and the barrier is reset so that it can be used again
  - `BrokenBarrierOperation`
  - Implementations - `CyclicBarrier`, `Exchanger`   


==Chapter 6 : Task Executions==
- Thread lifecycle is not cheap to manage
- When there are more runnable threads than processors, there are idle threads which eat up memory
- `XSS` JVM flag changes the thread stack size

## Executor Framework
- The primary abstraction for task execution in Java is not Thread, but rather the `Executor` framework
- Decouples task submission from task execution
- The Executor implementations also provide lifecycle support and hooks for adding statistics gathering, application management, and monitoring.
- Using an Executor is usually the easiest path to implementing a producer-consumer design in your application.
- Execution policies allow you to set the queues and rejection policies among other things for the executor
- Thread pools
  - `newFixedThreadPool` - increase size then constant
  - `newCachedThreadPool` - no size, can increase or decrease depending on the load
  - `newSingleThreadExecutor` - just a single thread with a backing LIFO queue
  - `newScheduledThreadPool` - supports delayed task execution
- Executor lifecycle   
