---
title: "Java Concurrency In Practice - Notes"
date: "2026-08-21"
lastmod:  "2026-08-22"
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


# ==Chapter 6 : Task Executions==
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
  - 3 states : `running`, `shutting down`, and `terminated`  
  - `ExecutorService` provides methods for lifecycle management
  - `shutdown()` method accepts no new tasks, prev are allowed to continue
  - `shutdownNow()` attempts to cancel outstanding tasks and does not start any tasks that are queued but not begun
  - post shutdown tasks are handled by `rejectedExecutionHandler`
  - use `while (executorService.awaitTermination()) {...}` to wait in a blocking fashion for tasks to finish post shutdown is requested. `isShutdown()` returns true as soon as shutdown is requested
- Delayed & Periodic Tasks
  - prefer ScheduledThreadPoolExecutor over Timer and TimerTask
  - TimerTask if it throws an exception, cancels the overall timer itself, new tasks can't be executed
  - can implement own scheduling service by wrapping around `DelayQueue`
- `Future` represents the lifecycle of a task
- `Future.get()` throws ExecutionException and CancellationException
- Submitting a runnable or callable to an executor constitutes safe publication from submitting thread to executing thread. Same for setting result in Future object.
- The real performance payoff of dividing a program’s workload into tasks comes when there are a large number of independent, homogeneous tasks that can be processed concurrently.
- `CompletionService` = `Executor` + `BlockingQueue`. Submit callable tasks and query upon it using `poll` and `take` methods.
- `ExecutorCompletionService` implements `CompletionService`

# ==Chapter 7 : Cancellation & Shutdown==

- Dealing well with failure, shutdown, and cancellation is one of the characteristics that distinguishes a well-behaved application from one that merely works.
- Cancellable activity : external code can drive activity to completion before natural completion. May be because of user requested cancellation, time limited activities, application events, external failures / errors, and application shutdown
- Interruption is the best way to implement cancellation policies since most concurrent APIs check for InterruptedException. They might not check for other external flags. There is nothing in the API or language specification that ties interruption to any specific cancellation semantics, but in practice, using interruption for anything but cancellation is fragile and difficult to sustain in larger applications.
- The JVM makes no guarantees on how quickly a blocking method will detect interruption, but in practice this happens reasonably quickly.
- Calling interrupt does not necessarily stop the target thread from doing what it is doing; it merely delivers the message that interruption has been requested. If a thread is interrupted when it is NOT blocked, it may be upto the client code itself to poll its status and do something with it. Try not to swallow it.
- Interruption is usually the most sensible way to implement cancellation.
- Task : Cancellation Policy <-> Threads : InterruptionPolicy
- Because each thread has its own interruption policy, you should not interrupt a thread unless you know what interruption means to that thread. A thread should only be interrupted by its owner.
- Only code that implements a thread’s interruption policy may swallow an interruption request. General-purpose task and library code should never swallow interruption requests.
- `boolean cancel(boolean mayInterruptIfRunning)` in `Future` : pass true if task can handle interruption, otherwise not
- The task execution threads created by the standard Executor implementations implement an interruption policy that lets tasks be cancelled using interruption, so it is safe to set `mayInterruptIfRunning` when cancelling tasks through their Futures when they are running in a standard Executor. You should not interrupt a pool thread directly when attempting to cancel a task, because you won’t know what task is running when the interrupt request is delivered—do this only through the task’s Future.
- When Future.get throws InterruptedException or TimeoutException and you know that the result is no longer needed by the program, cancel the task with Future.cancel.
- If a thread is blocked performing synchronous socket I/O or waiting to acquire an intrinsic lock, interruption has no effect other than setting the thread’s interrupted status. We have to explicitly convince them.
- 

