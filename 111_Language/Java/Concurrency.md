# Introduction

## What is multitasking?

- It is the Operating System's ability to have more than one program running at what seems like the same time.
- The OS assigns CPU time slices to each process, giving the impression of parallel activity.
- 
## What are multithreaded programs?

- These programs do multiple tasks at the same time. 
- Each task is executed in a thread.
- Programs that can run more than one thread at once are said to be multithreaded.

## Multiple Processes vs Multiple Threads
- The main diff is that each process has a complete set of its own variables, where as **threads share the same data**.
- However shared variables make communication between threads more efficient and easier to program than inter-process communication.
- Threads are more light-weight than processes, because it takes less overhead to create and destroy individual threads than processes.
- #### Examples of multithreading 
	- A web server needs to be able to serve concurrent requests.
	- A browser should be able to download simultaneously download multiple images.

# What are Threads ?

## Threads

- A Thread is a light weight process.
- A program is divided into some number of tasks that are to be executed at the same time.
- Each thread is assigned a task which it executes concurrently with other threads that are also running.

## How to create Threads in a program ?

### Approach 1:

Here is a simple procedure for running a task in a separate thread:

1. Place the code for the task into the `run method` of a class that implements the `Runnable interface`. That interface contains only a single method *(Runnable is a Functional Interface)*
``` Java
public interface Runnable { void run(); }
``` 

2. Since Runnable is a functional interface, you can make an instance with a lambda expression:
```Java
Runnable r = () -> { task code };
```

3. Construct a Thread object from the `Runnable`:
```Java
var t = new Thread(r);
```

4. Start the thread:
```Java
t.start();
```

### Approach 2:

- You can also define a thread by forming a subclass of the `Thread class`, like this:

```Java
class MyThread extends Thread { 
	public void run() {
		 task code 
	}
}
```
- Then you construct an object of the subclass and call its `start` method.
- However, this approach is no longer recommended. You should decouple the task that is to be run in parallel from the mechanism of running it. If you have many tasks, it is too expensive to create a separate thread for each of them. Instead, you can use a `thread pool`.

### Caution
- Never call the `run` method of the `Thread` class or the `Runnable` object directly.
- It will execute the task in the same thread in which the current program is running -- no new thread is started.
- Instead call the `Thread.start` method which creates a new thread that executes the `run` method.

## Thread Methods

### java.lang.Thread
- `Thread(Runnable target)` : constructs a new thread that calls the `run()` method of the specified target.
- `void start()` : starts this thread, causing the `run()` method to be called. This method will return immediately. The new thread runs concurrently.
- `void run()` : calls the `run` method of the associated `Runnable`.
- `static void sleep(long millis)` : sleeps for the given number of milliseconds.

### java.lang.Runnable
- `void run()` : must be overridden and supplied with instructions for the task that you want to have executed.

# Thread States

