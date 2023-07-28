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
## There are 6 thread states
1. New
2. Runnable
3. Blocked
4. Waiting
5. Timed Waiting
6. Terminated

- To find out the current state of a thread call `getState()` method.

![[Pasted image 20230728143422.png]]


### New Threads
- When you create a thread for example, `new Thread(r)` --- the thread is not yet running. This means that it is the **new** state.
- When a thread is in the new state, the program **has not started executing code inside of it**.

### Runnable Threads
- When the `start` method is invoked, the thread is in the **runnable** state.
- A runnable thread may or may not be running at any given time.
	- This is why the state is called “runnable” and not “running.”
- All modern desktop and server operating systems use **preemptive scheduling**. 
	- These systems give each runnable thread a slice of time to perform its task. When that slice of time is exhausted, the operating system preempts the thread and gives another thread an opportunity to work. ***When selecting the next thread, the operating system takes into account the thread priorities.***
- Small devices such as cell phones may use **cooperative scheduling**. 
	- In such a device, a thread loses control only when it calls the `yield` method, or when it is blocked or waiting.
#### java.lang.Thread
- `static void yield()` : Causes the currently executing thread to yield to another thread.

### Blocked and Waiting Threads
- When a thread is blocked or waiting, it is temporarily inactive. It is up to the scheduler to reactivate it. 
- The details depend upon how the inactive state was reached.
	- When the thread tries to acquire an intrinsic lock which is held by another thread, it becomes blocked.It becomes unblocked when all other threads have relinquished the lock and the scheduler has allowed this thread to hold it.
	- When a thread waits for another thread to notify the scheduler of a condition, it enters the waiting state. This happens by calling the `Object.wait` or `Thread.join` method.
	- Several methods have a timeout parameter( `Thread.sleep`, `Object.wait`, `Thread.join` etc). Calling them causes the thread to enter **Timed waiting state**. This state persists until the timeout expires or the appropriate notification has been received.

### Terminated Threads
A thread is terminated for one of two reasons:
1. The `run` method exits normally.
2. It dies abruptly because an **uncaught exception** terminates the `run `method.
3. you can kill a thread by invoking its `stop` method. 
	- That method throws a **ThreadDeath error object** that kills the thread. However, the stop method is deprecated, and you should never call it in your own code.
## Thread State Methods

### java.lang.Thread
- `void join()` : waits for the specified thread to terminate.
- `void join(long millis)` : waits for the specified thread to die or for specified number of milliseconds to pass.
- `Thread.state getState()` : gets the state of this thread
- `void stop()` : stops the thread. This method is deprecated.
- `void suspend()` : suspends this thread's execution. This method is deprecated.
- `void resume()` : resumes this thread. This is only valid after `suspend()` has been invoked. This method is deprecated.
- `void interrupt()` : This method can be used to request termination of a thread.
	- sends an interrupt request to a thread. The interrupted status of the thread is set to true. If the thread is currently blocked by a call to sleep, then an InterruptedException is thrown.
``` Java
while(!Thread.currentThread().isInterrupted() && more work to do){
	do more work
}
```
- `static boolean interrupted()` : Tests whether the current thread has been interrupted. Note that this is a static method. The call has a side effect—it resets the interrupted status of the current thread to false.
- `boolean isInterrupted()` : Tests whether a thread has been interrupted. Unlike the static interrupted method, this call does not change the interrupted status of the thread.
- `static Thread currentThread()` : Returns the Thread object representing the currently executing thread.




