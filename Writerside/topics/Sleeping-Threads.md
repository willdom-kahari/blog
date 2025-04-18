# Sleeping Threads

The `sleep()` method causes the current thread to suspend or pause execution for a specific period.<br />
Pausing the thread is an efficient means of making processor time available to other threads of an application or other applications.

```java
public static void main(String[] args) {
    try {
        Thread.sleep(milliseconds); // Pauses the current thread
    } catch (InterruptedException e) {
        Thread.currentThread().interrupt(); // Restore interrupted status
    }
}
```

### Usage
1. <b>Simulating Delay: </b>Creating artificial delays in thread execution
```java
public void run() {
    try {
        System.out.println("Task started");
        Thread.sleep(2000); // 2 second delay
        System.out.println("Task completed");
    } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
    }
}
```

2. <b>Rate Limiting: </b>Controlling the rate at which a thread performs operations
```java
public static void main(String[] args) {
    while (true) {
        performTask();
        Thread.sleep(1000); // Execute once per second
    }
}
```
3. <b>Coordination: </b>Giving other threads a chance to execute (Though not reliable for synchronisation)
```java
public void run() {
    while (!sharedResource.isReady()) {
        try {
            Thread.sleep(100); // Check every 100ms
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
            return;
        }
    }
    // Proceed with processing
}
```

- The `InterruptedException` is an exception that `sleep` throws when another thread interrupts the current thread while sleep is active

### Key Points
1. <b>Interruption Handling: </b>`sleep()` can be interrupted, hence the `InterruptedException` must be handled.
2. <b>Does Not Release Locks: </b>Unlike `wait()`, `sleep()` does not release any monitor locks it holds.
3. <b>Precision: </b>Sleep duration isn't guaranteed to be exact, it's minimum time.
4. Always restore interruption status when catching `InterruptedException`.
5. `sleep()` is a static method that always affects the current thread, not any arbitrary thread you might reference.
6. The `sleep()` method is overloaded:
    - `sleep(long millis)` - sleeps for specified milliseconds
    - `sleep(long millis, int nanos)` - sleeps with milliseconds + nanosecond precision

