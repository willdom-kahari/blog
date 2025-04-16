# Thread Lifecycle

A thread goes through various states during its lifecycle. The thread lifecycle is defined in the `Thread.State` enum in Java.

### NEW STATE
- <b>Description:</b>
    - A thread is in the <b>New</b> state when it is created but has not started yet.
    - At this point, the thread object is instantiated, but no system resources (like CPU cycles) are allocated it.
- <b>How to reach this state:</b>
    - By creating a thread instance using the `Thread` class or by implementing the `Runnable` interface

```java
Thread thread = new Thread(() -> {
    System.out.println("Thread is running ...");
});
```

- <b>Key Points:</b>
    - In this state, the thread is just an object and is not considered "alive".
    - Calling `thread.start()` moves the thread to the <b>Runnable</b> state.

### RUNNABLE STATE
- <b>Description:</b>
    - A thread enters the <b>Runnable</b> state after the `start()` method is called.
    - The thread is now "alive" and is eligible to be scheduled for execution by the thread scheduler.
    - <b>Runnable</b> does <b>not</b> mean the thread is running — it means the thread is ready to run but waiting for the CPU to assign time for execution.
- <b>How to reach this state:</b>
    - By calling the `start()` method on a thread object.

```java
thread.start(); // Thread is now in the Runnable state
```

- <b>Key Points:</b>
    - The thread scheduler (part of the JVM) determines when the thread transitions to the <b>Running</b> state.
    - The scheduling depends on factors like thread priority, CPU availability, and the operating system's scheduling algorithm.

### RUNNING STATE
- <b>Description:</b>
    - A thread ENTERS the <b>RUNNING</b> state when the thread scheduler selects it for execution.
    - In this state, the thread's `run()` method is actively executing.
- <b>How to reach this state:</b>
    - The thread scheduler moves a thread from the <b>Runnable</b> state the <b>Running</b> state.

```java
public void run(){
    System.out.println("Thread is running ...");
}
```

- <b>Key Points:</b>
    - A thread does not stay in the <b>Running</b> state indefinitely. It can be preempted or yield its execution back to the <b>Runnable</b> state.
    - Use the `Thread.yield()` to voluntarily give up the CPU and allow other threads to execute.

### BLOCKED
- <b>Description:</b>
    - A thread is in the <b>Blocked</b> state when it is waiting to acquire a lock or a resource that is held by another thread.
- <b>How to reach this state:</b>
    - Trying to enter a synchronised block or method while another thread is holding the lock

```java
synchronized(lock){
    // Thread acquires lock here
}
```

### WAITING
- <b>Description:</b>
    - A thread is in the <b>Waiting</b> state when it is waiting indefinitely for another thread to perform an action (e.g. notify it).
- <b>How to reach this state:</b>
    - By calling `Object.wait()`, `Thread.join()`, `LockSupport.park()` on an object (used in conjunction with `synchronized` blocks).

```java
synchronized(lock){
    lock.wait();
}
```

### TIMED WAITING
- <b>Description:</b>
    - A thread is in the Timed Waiting state when it is waiting for another thread to perform an action but only for a specified amount of time.
- <b>How to reach this state:</b>
    - By calling methods like `Thread.sleep()`, `wait(timeout)`, or `join(timeout)`.

```java
Thread.sleep(1000); // Thread sleeps for 1 second
```

- <b>Key Points:</b>
    - The thread will move back to the Runnable state once the blocking condition is resolved or the timeout expires.

### TERMINATED 
- <b>Description:</b>
    - A thread enters the Terminated state when it completes its execution or is explicitly stopped.
    - Once a thread is terminated, it cannot be restarted.
- <b>How to reach this state:</b>
    - When the `run()` method finishes or an uncaught exception occurs within the thread.

```java
public void run() {
    System.out.println("Thread execution completed");
}
```

- <b>Key Points:</b>
    - If a thread is in the <b>Terminated</b> state, calling `start()` on it again will throw `IllegalThreadStateException`.

### STATE TRANSITIONS
| Method              | State Transition        | Description                                                    |
|---------------------|-------------------------|----------------------------------------------------------------|
| start()             | 	New → Runnable	        | Starts the thread and moves it to the Runnable state.          |
| run()	              | Runnable → Running	     | Executes the thread's task when it is scheduled.               |
| sleep(milliseconds) | Running → Timed Waiting | Makes the current thread sleep for a specified duration.       |
| wait()              | 	Running → Waiting      | Causes the current thread to wait indefinitely until notified. |
| join()              | 	Running → Waiting      | 	Waits for another thread to finish its execution.             |
| notify()            | 	Waiting → Runnable     | 	Wakes up a single thread waiting on an object's monitor.      |
| notifyAll()         | 	Waiting → Runnable     | 	Wakes up all threads waiting on an object's monitor.          |
| yield()             | 	Running → Runnable     | 	Suggests to the scheduler to allow other threads to execute.  |

