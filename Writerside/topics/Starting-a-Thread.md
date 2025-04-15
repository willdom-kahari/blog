# Starting a Thread

An application that creates an instance of `Thread` must provide code that will run in that thread. There are two was to do this:
1. Provide a `Runnable` object.
2. Subclass `Thread`


### Providing a `Runnable` object
- `Runnable` is a functional interface that defines a single method `run()`, meant to contain the code to be executed in the thread.
- To use, implement the `Runnable` interface and pass it to the `Thread` object constructor.

```java
// implement the Runnable interface
class MyRunnable implements Runnable{
    @Override
    public void run(){
        System.out.println("Runnable is running: " + Thread.currentThread().getName());
    }
}

// Pass the Runnable Object to the Thread object constructor
public class Main{
    public static void main(String[] args) {
        // Create an instance of the object that implements Runnable
        var runnable = new MyRunnable(); 
        
        Thread t1 = new Thread(runnable);
        t1.start(); // starts a new thread
    }
}
```
`t1.start()` spawns a new thread and the thread executes the `run()` method

#### Key Characteristics {id="key-characteristics_1"}
1. Interface based — more flexible as Java allows implementing multiple interfaces.
2. Better design — follows the composition over inheritance principle.
3. Reusability — The same runnable can be executed by multiple threads.
4. Compatibility — required for working with the `ExecutorService` and other higher-level concurrency utilities.


### Subclassing `Thread`
- The `Thread` class itself implements `Runnable`, though its `run()` method does nothing.
- By subclassing it, you must provide your own implementation of `run()`.

```java
// extending the Thread class
class MyThread extends Thread{
    @Override
    public void run(){
        System.out.println("Thread subclass is running: " + Thread.currentThread().getName());
    }
}


public class Main{
    public static void main(String[] args) {
        Thread t1 = new MyThread();
        t1.start(); // starts a new thread
    }
}
```

#### Key Characteristics {id="key-characteristics_2"}
1. Inheritance based.
2. Single inheritance limitation - since Java doesn't support multiple inheritance, extending `Thread` means your class can't extend any other class.
3. Direct control - provides direct methods for thread management like `start()`, `sleep()`, etc.


### Key Differences
| Feature                | Thread                                      | Runnable                                            |
|------------------------|---------------------------------------------|-----------------------------------------------------|
| Type                   | Class (extends `Thread`)                      | Interface (implements `Runnable`)                   |
| Inheritance Limitation | Cannot extend another class                 | Can extend another class                            |
| Memory Usage           | Heavier (each thread is an object)          | Lighter (can share Runnable instances)              |
| Reusability            | Less reusable (thread dies after execution) | Highly reusable (can be passed to multiple threads) |
| Thread Control         | Direct access to thread methods             | Requires a `Thread` object for control              |
| Lambda Support         | No (since it's a class)                     | Yes (functional interface)                          |
| Executor Compatibility | Not directly usable in `ExecutorService`      | Directly usable in `ExecutorService`                |


### Best Practices
1. Prefer `Runnable` over `Thread` extensions
2. Keep `run()` methods short — should represent discrete tasks.
3. Prefer `ExecutorService` over manual thread management (thread pools)
4. Name your threads for debugging
5. Handle exceptions properly — use try-catch blocks.
6. Make thread-safe when sharing data between runnables.
7. Handle interrupts properly
8. Minimise synchronisation scope
9. Consider higher level concurrency utilities
    - `Future`
    - `Lock` objects
    - `ConcurrentHashmap`
