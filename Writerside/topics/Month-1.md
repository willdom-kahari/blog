# 📅 Month 1: Thread Basics & Synchronization

<b>Goal:</b> Understand thread creation, lifecycle, and basic synchronisation.

## Week 1-2: Thread Fundamentals
- <b>Learn:</b>
  - `Thread` vs `Runnable`
  - Thread states (`NEW`, `RUNNABLE`, `WAITING`, etc.)
  - `join()`, `sleep()`, `yield()`

- <b>Code Katas:</b>
    - Create 10 threads, each print 1–100 sequentially (observe interleaving).
    - Make Thread-2 wait for Thread-1 to finish using join().(thread coordination) 
    - Create a thread that sleeps but can be interrupted.

- <b>Projects to Build:</b> 
  1. Multi-Threaded Counter
        - Create a counter incremented by multiple threads (demonstrate race condition).
        - Fix it using `synchronized`.
  2. Thread Status Monitor
        - A program that spawns threads and logs their states (NEW, RUNNABLE, WAITING, etc.)
  3. Thread Scheduler Simulation
        - Simulate thread scheduling using sleep(), yield(), and join().

- <b>Projects to Study</b>
    - [Guava’s](https://github.com/google/guava) Striped class (for lock striping)
    - [Java’s](https://hg.openjdk.org/jdk8/jdk8/jdk/file/tip/src/share/classes/java/lang/Thread.java) Thread class (study the source code)


## Week 3-4: Synchronization & Locks
- <b>Learn:</b>
  - `synchronized` methods/blocks
  - `volatile` keyword
  - `wait()`, `notify()`, `notifyAll()`

- <b>Code Katas:</b>
    - Two threads increment a shared counter (use synchronized).
    - Thread-1 prints "Ping", Thread-2 prints "Pong" (alternate using wait()/notify())
    - Create a deadlock with two threads and two locks, then resolve it.

- <b>Projects to Build:</b> 
  1. Thread-Safe Queue
        - Implement a blocking queue using wait()/notify().
  2. Producer-Consumer Problem
        - Producers add items, consumers remove them (use synchronized).
  3. Bank Account Simulation
        - Multiple threads deposit/withdraw, ensure no race conditions.

- <b>Projects to Study</b>
    - [Apache Kafka’s](https://github.com/apache/kafka) Producer-Consumer Model (high-level study)
    - [Java’s](https://hg.openjdk.org/jdk8/jdk8/jdk/file/tip/src/share/classes/java/util/concurrent/ArrayBlockingQueue.java) ArrayBlockingQueue

📚 <b>Resources:</b>
- Oracle’s Java Threads Tutorial
- Java Concurrency in Practice (Ch. 1–5)
- Effective Java (Item 78–81)
