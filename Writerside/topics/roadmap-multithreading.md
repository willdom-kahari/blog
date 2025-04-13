# 📅 100-Day Multithreading in Java Mastery Plan

**Daily Commitment**: 1-2 hours (theory + hands-on)  
**Resources**:
- [Java Concurrency in Practice (JCIP)](https://jcip.net/) (Primary Book)
- [Baeldung Concurrency Guide](https://www.baeldung.com/java-concurrency) (Cheat Sheet)
- [LeetCode Concurrency Problems](https://leetcode.com/tag/concurrency/) (Practice)

---

## 🌟 **Phase 1: Foundations (Days 1-20)**
### Week 1: Thread Basics
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 1   | Thread vs Runnable            | Hello Threads (5 threads in order)    | [Oracle Thread Tutorial](https://docs.oracle.com/javase/tutorial/essential/concurrency/) |
| 2   | Thread Lifecycle              | Thread ID Printer                    | [Telusko Video](https://youtu.be/6HydEs65Utk) |
| 3   | Race Conditions               | Unsafe Counter Demo                  | JCIP Ch.1                                  |
| 4   | `sleep()`, `join()`           | Countdown Timer                      | [Baeldung Guide](https://www.baeldung.com/java-thread-join) |
| 5   | Daemon Threads                | Background Logger                    | [Daemon Threads](https://www.baeldung.com/java-daemon-thread) |

### Week 2: Synchronization
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 6   | `synchronized` Methods        | Bank Account Simulator               | JCIP Ch.2                                  |
| 7   | `volatile` Keyword            | Flag-Based Thread Stopper            | [Jenkov Video](https://youtu.be/WH5UvQJizH0) |
| 8   | Deadlocks                     | Deadlock Simulator                   | [jstack Guide](https://www.baeldung.com/java-thread-dump) |
| 9   | `wait()/notify()`             | Ping-Pong Game                       | [Producer-Consumer Code](https://github.com/eugenp/tutorials/tree/master/core-java-modules/core-java-concurrency-basic) |
| 10  | `ReentrantLock`               | ATM Withdrawal System                | [Java Brains Video](https://youtu.be/ahBC69_iyk4) |

---

## 🚀 **Phase 2: Concurrency API (Days 21-50)**
### Week 3: Executors
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 11  | `ExecutorService`              | File Processor (100 files)            | [Baeldung Thread Pools](https://www.baeldung.com/thread-pool-java-and-guava) |
| 12  | `Future`/`Callable`            | Factorial Calculator                 | JCIP Ch.6                                  |
| 13  | `CompletableFuture`            | Async Weather API Fetcher            | [Devoxx Video](https://youtu.be/-MBPQ7NIL_Y) |

### Week 4: Concurrent Collections
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 14  | `ConcurrentHashMap`            | Word Frequency Counter               | JCIP Ch.5                                  |
| 15  | `BlockingQueue`                | Chat Message Buffer                  | [Baeldung Guide](https://www.baeldung.com/java-blocking-queue) |
| 16  | `CountDownLatch`               | Exam Start Synchronizer              | [JavaDoc](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CountDownLatch.html) |

---

## 🔥 **Phase 3: Advanced (Days 51-80)**
### Week 5: Performance
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 17  | `ForkJoinPool`                 | Parallel Fibonacci                   | [Oracle Guide](https://docs.oracle.com/javase/tutorial/essential/concurrency/forkjoin.html) |
| 18  | ThreadLocal                    | User Session Manager                 | [Baeldung](https://www.baeldung.com/java-threadlocal) |

### Week 6: Real-World Apps
| Day | Topic                          | Project/Kata                          | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 19  | Rate Limiting                  | API Call Throttler                   | [Semaphore Kata](#)                        |
| 20  | Caching                        | LRU Cache with Locks                 | [GitHub Example](https://github.com/Suryakant-Bharti/Java-MultiThreading-Projects) |

---

## 🏆 **Phase 4: Mastery (Days 81-100)**
### Week 7: Capstone Projects
| Day | Topic                          | Project                               | Resources                                  |
|-----|--------------------------------|---------------------------------------|--------------------------------------------|
| 21  | High-Performance Server        | Netty Chat Server                    | [Netty Tutorial](https://youtu.be/wjkQ8idURK8) |
| 22  | Distributed Systems            | Task Queue (Celery-like)             | [RabbitMQ Guide](https://www.rabbitmq.com/tutorials/tutorial-one-java.html) |

---

## 📌 **Weekly Checklist**
- **Monday-Wednesday**: Study theory + small katas
- **Thursday-Friday**: Hands-on projects
- **Saturday**: Debugging/optimization (jstack, VisualVM)
- **Sunday**: LeetCode problem (e.g., [Print FooBar Alternately](https://leetcode.com/problems/print-foobar-alternately/))

**Pro Tip**: Bookmark [Java Concurrency FAQ](http://www.ibm.com/developerworks/java/library/j-concurrency-faq/) for quick reference.
