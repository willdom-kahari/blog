# 📅 Month 2: java.util.concurrent & Thread Pools
<b>Goal:</b> Master ExecutorService, thread pools, and concurrent utilities.

## Week 5-6: Executors & Thread Pools
- <b>Learn:</b>
  - ExecutorService (FixedThreadPool, CachedThreadPool)
  - Future and Callable

- <b>Code Katas:</b>
    1. Fibonacci with Future
        - Compute Fibonacci(n) by splitting work across threads (e.g. divide and conquer)
        - Compare performance vs single-threaded.
    2. Thread Pool-Based Web Scraper Simulator
        - Mock fetching URLs with random delays.
        - Use Future to aggregate results.
    3. Task Scheduler
        - Simulate scheduled tasks (e.g., ScheduledExecutorService) with fixed-rate delays.

- <b>Projects to Build:</b> 
  1. Parallel File Downloader
        - Download multiple files concurrently using FixedThreadPool.
        - Track progress with Future and display download stats.
        - (Advanced) Add retry logic for failed downloads.
  2. Web Crawler (Simplified)
        - Use CachedThreadPool to crawl web pages (or mock URLs) in parallel.
        - Limit depth/crawl scope to avoid infinite recursion.
        - (Bonus) Store results in a thread-safe collection.
  3. Batch Image Processor
        - Resize/convert multiple images in parallel using ExecutorService.
        - Use Future to track completion of each task.

- <b>Projects to Study</b>
    - [OkHttp](https://github.com/square/okhttp) - study how it uses thread pools for asynchronous HTTP calls
    - Apache Commons HttpClient: look at its threading model for connection pooling.
    - Guava's ListeningExecutorService: learn how it extends ExecutorService for callback-based tasks.


## Week 7-8: Concurrent Collections & Atomic Classes
- <b>Learn:</b>
  - ConcurrentHashMap, CopyOnWriteArrayList
  - AtomicInteger, AtomicReference

- <b>Code Katas:</b>
    1. Thread-Safe LRU Cache
        - Implement a TTL (time-to-live) eviction policy.
    2. Atomic Bank Transfer
        - Simulate transfers between accounts using AtomicInteger.
    3. Producer-Consumer with BlockingQueue
        - Use ArrayBlockingQueue to pass data between threads.
    4. Adder/Counter Metrics
        - Benchmark AtomicLong vs LongAdder under high contention.

- <b>Projects to Build:</b> 
  1. Thread-Safe Cache with ConcurrentHashMap
        - Implement a TTL (time-to-live) eviction policy.
        - (Advanced) Use computeIfAbsent for atomic operations.
  2. High-Frequency Event Counter
        - Track events (e.g. API hits) per second using AtomicInteger.
        - (Bonus) Add sliding window logic.
  3. Bank Transfer Simulator
        - Use AtomicReference or synchronized to handle account balances.
        - Simulate concurrent transfers with thread safety.

- <b>Projects to Study</b>
    - [Caffeine Cache](https://github.com/ben-manes/caffeine) - Study its ConcurrentHashMap-based caching.
    - [Netty](https://github.com/netty/netty) - Look at how it uses atomic classes for state management.
    - [Disruptor](https://github.com/LMAX-Exchange/disruptor) - High-performance ring buffer using atomic operations.

- <b>Bonus Challenges</b>
    - Combine Concepts:<br />
        Build a stock price aggregator that:<br />
            1. Fetches prices concurrently (thread pools + Future).<br />
            2. Stores results in a ConcurrentHashMap.<br />
            3. Uses AtomicReference for real-time updates.
  - Debugging:
        Inject thread-safety bugs (e.g., race conditions) and practice fixing them.
  
📚 <b>Resources:</b>
      - Java java.util.concurrent Javadocs
      - Java Concurrency in Practice (Ch. 5–6)
      - Effective Java (Concurrency Items)

