# 📅 Month 3: Advanced Synchronization & Performance
<b>Goal:</b> Deep dive into locks, deadlocks, and performance tuning.

## Week 9-10: Locks (ReentrantLock, ReadWriteLock)
- <b>Learn:</b>
  - ReentrantLock vs synchronized
  - ReadWriteLock for high-read scenarios

- <b>Code Katas:</b>
  1. ReentrantLock vs Synchronized Benchmark
      - Compare performance between synchronized and ReentrantLock in a high-contention scenario.

  2. ReadWriteLock for a Thread-Safe Dictionary
      - Implement a dictionary where reads are lock-free but writes are exclusive.

  3. Dining Philosophers with Timeout
      - Extend the solution using tryLock() to avoid indefinite waiting.

- <b>Projects to Build:</b> 
  1. Thread-Safe LRU Cache with ReadWriteLock
      - Implement the Least Recently Used (LRU) cache where reads are frequent, and writes are rare.
      - Use ReentrantReadWriteLock to optimize concurrency.

  2. Rate Limiter using ReentrantLock
      - Build a rate limiter that allows a fixed number of requests per second.
      - Use ReentrantLock with Condition for throttling.

  3. Dining Philosophers Problem
      - Solve the classic concurrency problem using ReentrantLock to prevent deadlocks.


- <b>Projects to Study</b>
  1. [Guava’s](https://github.com/google/guava) Cache Implementation
      - Study how Google Guava uses ReadWriteLock in its caching mechanism.

  2. [Netty’s](https://github.com/netty/netty) EventLoop & Thread Model
      - Analyze how Netty handles thread-local optimizations.


## Week 11-12: Deadlocks & Performance
- <b>Learn:</b>
  - How to detect & avoid deadlocks
  - ThreadLocal for per-thread storage

- <b>Code Katas:</b>
  1. Deadlock Detection & Recovery
      - Write a program that intentionally deadlocks, then use ThreadMXBean to detect and resolve it.
  2. Optimize a Counter with LongAdder
      - Replace AtomicLong with LongAdder in a high-write scenario and measure performance.
  3. ThreadLocal for Context Propagation
      - Simulate a logging system where each thread has its own MDC (Mapped Diagnostic Context).

- <b>Projects to Build:</b> 
  1. Thread-Safe Transaction Manager
- Simulate a banking system where multiple threads transfer money between accounts.
- Use ReentrantLock with tryLock() to avoid deadlocks.

  2. Lock Striping for High-Concurrency HashMap
      - Optimize a HashMap by partitioning it into segments, each with its own lock.
      - Compare performance against ConcurrentHashMap.

  3. ThreadLocal-Based User Session Manager
      - Use ThreadLocal to store per-thread session data in a web server mockup.

- <b>Projects to Study</b>
    - [Apache Kafka’s](https://github.com/apache/kafka) Partition-Level Locking - Investigate how Kafka uses lock striping for high-throughput message queues.
    - Java’s ConcurrentHashMap - Study the lock striping and fine-grained synchronisation techniques.

📚 <b>Resources:</b>
- Java Memory Model (JSR 133)
- Java Concurrency in Practice (Ch. 10–11) – Focus on lock optimisations and deadlock avoidance.
- Effective Java (Item 81) – Prefer Concurrent utilities over wait/notify.
