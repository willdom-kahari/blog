# 🗓️ 100-Day Java Multithreading Mastery Calendar

## 📌 Legend
- **Project**: Hands-on implementation
- **Kata**: Focused coding exercise
- **Resources**: Learning materials

---

## 🌱 **Phase 1: Foundations (Days 1-20)**
### Week 1: Thread Basics
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 1   | Thread vs Runnable  | **Project**: Ordered "Hello Threads" printer<br>**Kata**: Sequential thread execution | [Oracle Thread Docs](https://docs.oracle.com/javase/tutorial/essential/concurrency/) |
| 2   | Thread Lifecycle    | **Project**: Thread state visualizer<br>**Kata**: Simulate `NEW`→`TERMINATED` transitions | [Telusko Video](https://youtu.be/6HydEs65Utk) |
| 3   | Race Conditions     | **Project**: Broken counter<br>**Kata**: Fix with `synchronized` | JCIP Ch.2 |
| 4   | `sleep()`/`join()`  | **Project**: Parallel countdown timer<br>**Kata**: Sync threads with `join()` | [Baeldung Guide](https://www.baeldung.com/java-thread-join) |
| 5   | Daemon Threads      | **Project**: JVM shutdown hook<br>**Kata**: Logging daemon | [Daemon Threads](https://www.baeldung.com/java-daemon-thread) |

### Week 2: Synchronization
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 6   | `synchronized`      | **Project**: Bank account simulator<br>**Kata**: Prevent overdrafts | [JavaPoint](https://www.javatpoint.com/synchronization-in-java) |
| 7   | `volatile`          | **Project**: Flag-based thread stopper<br>**Kata**: Visibility demo | [Jenkov Video](https://youtu.be/WH5UvQJizH0) |
| 8   | Deadlocks           | **Project**: Dining philosophers<br>**Kata**: Detect with `jstack` | [FastThread](https://fastthread.io/) |
| 9   | `wait()`/`notify()` | **Project**: Producer-consumer (1:1)<br>**Kata**: Ping-pong game | [GitHub Example](https://github.com/eugenp/tutorials/tree/master/core-java-modules/core-java-concurrency-basic) |
| 10  | `ReentrantLock`     | **Project**: ATM with fair locking<br>**Kata**: Benchmark vs `synchronized` | [Java Brains](https://youtu.be/ahBC69_iyk4) |

---

## ⚙️ **Phase 2: Concurrency API (Days 21-50)**
### Week 3: Executors
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 11  | `ExecutorService`   | **Project**: File processor (100 files)<br>**Kata**: Compare pool types | [Baeldung Thread Pools](https://www.baeldung.com/thread-pool-java-and-guava) |
| 12  | `Future`/`Callable` | **Project**: Parallel factorial calculator<br>**Kata**: Timeout handling | JCIP Ch.6 |
| 13  | `CompletableFuture` | **Project**: Weather API aggregator<br>**Kata**: Chain async tasks | [Devoxx](https://youtu.be/-MBPQ7NIL_Y) |

### Week 4: Concurrent Collections
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 14  | `ConcurrentHashMap` | **Project**: Word frequency counter<br>**Kata**: Atomic updates | JCIP Ch.5 |
| 15  | `BlockingQueue`     | **Project**: Log message buffer<br>**Kata**: Implement producer-consumer | [Baeldung](https://www.baeldung.com/java-blocking-queue) |
| 16  | `CountDownLatch`    | **Project**: Multi-threaded test runner<br>**Kata**: Simulate race start | [JavaDoc](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/CountDownLatch.html) |

---

## 🚀 **Phase 3: Advanced (Days 51-80)**
### Week 5: Performance
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 17  | `ForkJoinPool`      | **Project**: Merge sort<br>**Kata**: Fibonacci benchmark | [Oracle Guide](https://docs.oracle.com/javase/tutorial/essential/concurrency/forkjoin.html) |
| 18  | `ThreadLocal`       | **Project**: User session store<br>**Kata**: Context propagation | [Baeldung](https://www.baeldung.com/java-threadlocal) |

### Week 6: Real-World Apps
| Day | Topic               | Project/Kata                          | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 19  | Rate Limiting       | **Project**: API throttler<br>**Kata**: Sliding window counter | [Semaphore Docs](https://docs.oracle.com/javase/8/docs/api/java/util/concurrent/Semaphore.html) |
| 20  | Caching             | **Project**: LRU cache<br>**Kata**: TTL expiration | [GitHub Example](https://github.com/Suryakant-Bharti/Java-MultiThreading-Projects) |

---

## 🏆 **Phase 4: Mastery (Days 81-100)**
### Week 7: Capstone Projects
| Day | Topic               | Project                               | Resources                                  |
|-----|---------------------|---------------------------------------|--------------------------------------------|
| 21  | High-Performance    | **Netty chat server**<br>**Kata**: Handle 10k connections | [Netty Tutorial](https://youtu.be/wjkQ8idURK8) |
| 22  | Distributed Systems | **Task queue** (Celery-like)<br>**Kata**: Retry failed jobs | [RabbitMQ](https://www.rabbitmq.com/tutorials/tutorial-one-java.html) |

---

## 📅 **Weekly Structure**
```mermaid
gantt
    title Weekly Plan
    dateFormat  YYYY-MM-DD
    section Week 1
    Theory       :a1, 2023-10-01, 3d
    Katas        :a2, after a1, 2d
    Project      :a3, after a2, 2d
    Debugging    :a4, after a3, 1d
