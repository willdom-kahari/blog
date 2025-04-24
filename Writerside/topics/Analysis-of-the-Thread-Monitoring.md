# Thread Status Monitor Implementation Analysis
This Java program demonstrates a thread visualizer that monitors and displays the states of multiple worker threads with different behaviors. Let me explain the concepts and strategy behind this implementation:

## Core Concepts
**Thread States Monitoring:** The program tracks thread states (NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING, TERMINATED) using Java's built-in Thread.getState() method.

**Multiple Thread Behaviours:** It creates 5 worker threads with distinct behaviors to demonstrate different thread states:
- Quick task completion
- Long wait using wait()
- Intermittent work with sleep intervals
- Two threads competing for a shared lock

**Daemon Monitoring Thread:** A separate monitoring thread periodically checks and reports the states of all worker threads.

## Implementation Strategy

### Shared Resources:
- `sharedLock:` An object used for synchronization between threads 4 and 5
- `monitoredThreads:` A list keeping track of all worker threads

### Worker Threads:
- **Worker-1:** Demonstrates a quick task (200ms) that terminates quickly
- **Worker-2:** Shows WAITING state by calling wait(5000)
- **Worker-3:** Demonstrates TIMED_WAITING with periodic sleep between work iterations
- **Worker-4 & Worker-5:** Compete for the sharedLock to demonstrate BLOCKED state

### Monitor Thread:
- Runs as a daemon thread (won't prevent JVM shutdown)
- Continuously polls thread states every second
- Prints formatted output showing each thread's name and state

### Key Design Choices

#### Synchronization:
- Uses object monitors (synchronized blocks) to demonstrate BLOCKED state
- Shows how threads wait for locks and how this affects their state

#### Timing:
- Worker threads have different durations to show state transitions over time
- Main thread sleeps for 15 seconds to allow observation of state changes

#### Error Handling:
- Properly handles InterruptedException by restoring interrupt status

#### Educational Value
This implementation serves as an excellent visualizer for understanding:
- How threads transition between different states
- The impact of synchronization on thread states
- How wait() differs from sleep()
- How daemon threads behave
- Practical observation of thread concurrency

The output would show real-time state changes, helping developers understand thread behavior in concurrent applications.

### Monitored Threads List
The monitoredThreads list plays a central role in this thread visualization system, serving as the registry that connects worker threads with the monitoring thread. Here's why it's necessary and how it functions:

#### Key Roles of monitoredThreads:
**Centralized Tracking:**
- Acts as a shared repository where all worker threads are registered
- Without it, the monitor thread would have no way to know which threads to observe

**State Observation Bridge:**
- Provides the monitoring thread access to all worker thread references
- Enables the monitor to call getState() on each thread

**Lifecycle Management:**
- Maintains references even after threads start (preventing garbage collection of thread objects)
- Allows observation until threads terminate

#### Why It's Necessary:
**Thread Isolation:**
- Java threads don't automatically expose themselves to observers
- Without explicit registration, the monitor couldn't discover worker threads

**Dynamic Monitoring:**
- The list allows adding/removing threads dynamically (though not implemented here)
- Supports monitoring an arbitrary number of threads

**State Comparison:**
- Enables comparing states across all threads simultaneously
- Shows how thread states relate to each other (e.g. one BLOCKED while another holds a lock)

#### Implementation-Specific Behavior:
**Registration:**
```java
Thread thread = new Thread(new WorkerThread(i), "Worker-" + i);
monitoredThreads.add(thread);  // Registration happens before thread starts
```
**Monitoring:**
```java
for (Thread thread : monitoredThreads) {
    System.out.printf("%-10s: %s%n", thread.getName(), thread.getState());
}
```

**Thread Safety Considerations:**
- The list is only modified by the main thread during setup (thread-safe in this case)
- Concurrent reads by the monitor thread don't require synchronization here
- If dynamic thread addition/removal were needed, concurrent access protection would be required
