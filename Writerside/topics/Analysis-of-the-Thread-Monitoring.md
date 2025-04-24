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
