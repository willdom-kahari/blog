# Joining Threads

The `join()` method is used to wait for a thread to complete its execution before continuing with the current (calling thread).<br/>
It is a crucial method for thread synchronisation.

```java
public static void main(String[] args) {
    Thread thread = new Thread(()-> {
        // Target thread doing a specific task
    });
    thread.start();
    thread.join(); // The current thread i.e. the main thread waits for the target thread to finish execution
}
```

### <b>Example:</b> The kata associated with these notes 
```java
public class Kata2 {
    public static void main(String[] args) throws InterruptedException {
        Thread first = new Thread(new NumbersPrinter(), "First thread");
        Thread second = new Thread(new NumbersPrinter(), "Second thread");
        
        first.start();  // Start first thread
        second.start(); // Start second thread immediately
        
        // Main thread waits for both to finish
        first.join();
        second.join();
        
        System.out.println("Both threads completed");
    }
}

class NumbersPrinter implements Runnable {
    @Override
    public void run() {
        for (int i = 0; i < 100; i++) {
            System.out.println(Thread.currentThread().getName() + ": counter = " + (i + 1));
        }
    }
}
```
- <b>Concurrent execution: </b>Both threads run simultaneously (interleaved output)
- <b>Main Thread Waits: </b>The main thread waits for both threads to finish.

### Key Points About `join()`
1. Blocks the calling thread until the target thread completes execution.
2. Throws InterruptedException if the current thread is interrupted while waiting.
3. The `join()` method is overloaded:
    - `join()` - waits indefinitely
    - `join(long millis)` - waits for specified milliseconds
    - `join(long millis, int nanos)` - waits with milliseconds + nanosecond precision


### Usage
1. <b>Waiting for initialisation: </b>Ensure background threads complete setup before proceeding.
2. <b>Resource cleanup: </b>Wait for worker threads to finish before shutting down.
3. <b>Result aggregation: </b>Collect results from multiple worker threads
