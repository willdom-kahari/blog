# Thread Interrupts

A thread interrupt is a signal sent to a thread, requesting it to stop or change its behaviour.<br />
Java threads are not forcibly terminated. Instead, they must cooperatively responds to the interrupt.<br />
The interrupt mechanism is built on the principle of graceful termination, where the interrupted thread is responsible for stopping itself.

### Interrupt Status
The interrupt mechanism is implemented using an internal flag known as the interrupt status.
Here is how it behaves:
- When the `interrupt()` method is called on a thread, the thread's interrupt status is set to `true`.
- The status can be queried with `isInterrupted()`.
- It can be cleared to `false` when
    1. The thread calls `Thread.interrupted()` or
    2. The thread is in a blocking state (e.g. `Thread.sleep()`, `wait()`, `join()`) and catches an `Interrupted exception`. 

### Interrupting a Running Task
When a thread is running (not blocked), it does not immediately stop its execution. The thread must:
- Periodically check its interrupt status using `Thread.currentThread().isInterrupted()`.
- Exit gracefully if it detects the interrupt signal.
```java
for (int i = 0; i < inputs.length; i++) {
    heavyCrunch(inputs[i]);
    if (Thread.currentThread().isInterrupted()) {
        // We've been interrupted: no more crunching.
        return; // alternatively for loops you can use the break statement depending on use case
    }
}
```
For complex cleanup:

```java
public void run() {
    try {
        while (!Thread.currentThread().isInterrupted()) {
            // Phase 1: Normal operation
        }
    } finally {
        // Phase 2: Cleanup after interruption
        releaseResources();
    }
}
```

### Interrupting a Blocked Thread
When a thread is in a blocking state:
1. Immediately throw an `InterruptedException`.
2. Clear the thread's interrupt status to `false`.
3. Restore the interrupt status

```java
try {
    Thread.sleep(1000);
} catch (InterruptedException e) {
    // Restore the interruption status
    Thread.currentThread().interrupt();
    
    // Option 1: Propagate by exiting
    return; 
    
    // Option 2: Rethrow as RuntimeException
    throw new RuntimeException("Thread interrupted", e);
}
```

#### Why Restore the Flag?
1. Preserving Interruption Intent
When InterruptedException is caught:

- The flag has already been cleared
- Restoring it ensures:
  - Other code up the call stack knows about the interruption
  - Proper thread cancellation can still occur

2. Maintaining Cooperative Cancellation
Java uses cooperative interruption:
- Threads aren't forced to stop
- They choose to respect interruption
- Without the flag, interruption signals get lost

### Interruption Policies
Define clear policies for different thread types:

| Thread Type     |	Interruption Policy |
|-----------------|---------------------|
| Worker Thread	  |Stop processing immediately|
| Network Thread	 |Close connections gracefully|
| GUI Thread	     |Ignore interrupts|
