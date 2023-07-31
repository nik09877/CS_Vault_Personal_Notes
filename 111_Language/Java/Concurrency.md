# Introduction

## What is multitasking?

- It is the Operating System's ability to have more than one program running at what seems like the same time.
- The OS assigns CPU time slices to each process, giving the impression of parallel activity.

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





# Thread Properties

## Daemon Threads
- A Daemon thread is simply a thread whose only purpose in life is to serve others.
	- Examples are timer threads that send regular "timer ticks" to other threads
	- Threads that clean up state cache entries.
- When only Daemon threads remain, the virtual machine exits.
- Turn a thread into Daemon thread by calling `t.setDaemon(true);`

## Thread Names
- Set any name with `setName` method:
```Java
var t = new Thread(runnable);
t.setName("web crawler");
```

## What is a Thread Group ?
- A thread group is a collection of threads that can be managed together.
- By default all threads that you create belong to the same `Thread group`.

## Thread Priorities
- In Java, every thread has a *priority*.
- A thread inherits the priority of the thread that created it.
- You can increase or decrease the priority using `setPriority()` method.
- The Priority value should be in the range `MIN_PRIORITY(defined as 1)` and `MAX_PRIORITY(defined as 10)`.
- `NORM_PRIORITY` is defined as 5.
- Thread priorities are highly system dependent.
	- Windows has 7 priority levels. Some  of the Java priorities will map to the same OS level.
	- In Oracle JVM for Linux, all threads have the same priority.

# Synchronization

## What is Race Condition ?
- When the output depends on the order in which the data are accessed and manipulated, it is called **race condition**.
- So the objective is to *synchronize the access*.

## Lock Objects

There are **two methods** for protecting a code block from concurrent access.
1. `synchronized` keyword
2. `ReentrantLock` class

### Using ReentrantLock class
`java.util.concurrent` framework provides separate classes for these mechanisms.

Syntax:

```Java
myLock.lock(); //a ReentrantLock object
try{
	//critical section
}
finally{
	myLock.unlock(); 
	//make sure the lock is unlocked even if an exception has occurred
}
```

Explanation:
-  This guarantees that **only one thread at a time** can enter the critical section.
-  When other threads call `lock`, they are deactivated until the first thread unlocks the lock object.
- If the code in the critical section throws an exception, the lock must be unlocked. Otherwise, the other threads will be blocked forever.

#### In depth Example
Let us use a lock to protect the transfer method of the Bank class.

```Java
public class Bank { 
	private var bankLock = new ReentrantLock();
	. . .
	public void transfer(int from, int to, int amount){
		bankLock.lock();
		 try { 
			 System.out.print(Thread.currentThread());
			 accounts[from] -= amount;
			 System.out.printf(" %10.2f from %d to %d", amount, from, to); 
			 accounts[to] += amount; 
			 System.out.printf(" Total Balance: %10.2f%n", getTotalBalance());
		  }
		finally { 
			bankLock.unlock();
		}
	 } 
}
```

**Explanation** : Suppose one thread calls transfer and gets preempted before it is done. Suppose a second thread also calls transfer. The second thread cannot acquire the lock and is blocked in the call to the lock method. It is deactivated and must wait for the first thread to finish executing the transfer method. When the first thread unlocks the lock, then the second thread can proceed

**Note** : Note that each Bank object has its own ReentrantLock object. If two threads try to access the same Bank object, then the lock serves to serialize the access. However, if two threads access different Bank objects, each thread acquires a different lock and neither thread is blocked. This is as it should be, because the threads cannot interfere with one another when they manipulate different Bank instances.


#### Note
- The lock is called **Reentrant** because a thread can repeatedly acquire a lock that it already owns (through recursion or calling other methods that have the same lock).
- The lock has a **hold count** that keeps track of the nested calls to the `lock` method. The thread has to call `unlock` for every call to `lock` in order to release the lock.
- So Code protected by a lock can call another method that uses the same locks.
- `ReentrantLock(boolean fair)` : constructs a lock with the given fairness policy. A fair lock favors the thread that has been waiting for the longest time. However, this fairness guarantee can be a significant drag on performance. Therefore, by default, locks are not required to be fair.
	- It sounds nice to be fair, but fair locks are a lot slower than regular locks. You should only enable fair locking if you truly know what you are doing and have a specific reason to consider fairness essential for your program. Even if you use a fair lock, you have no guarantee that the thread scheduler is fair. If the thread scheduler chooses to neglect a thread that has been waiting a long time for the lock, it doesn’t get the chance to be treated fairly by the lock.

#### Condition objects
- Sometimes a thread enters a critical section, only to find out that it can't proceed until certain condition is fulfilled.
- In this case a condition **object/condition variable** is used to manage threads that have acquired a lock but can't do useful work.
##### In depth Example
- Let us refine our simulation of the bank. We do not want to transfer money out of an account that does not have the funds to cover the transfer.
- Now, what do we do when there is not enough money in the account? We wait until some other thread has added funds. But this thread has just gained exclusive access to the `bankLock`, so no other thread has a chance to make a deposit. This is where condition objects come in.
- A lock object can have one or more associated condition objects.
- You obtain a condition object with the `newCondition` method.

###### Code:

```Java
package synch;
import java.util.*;
import java.util.concurrent.locks.*;

public class Bank
{
	private final double[] accounts;
	private Lock bankLock;
	private Condition sufficientFunds;
	
	public Bank(int n, double initialBalance)
	{
		accounts = new double[n];
		Arrays.fill(accounts, initialBalance);
		bankLock = new ReentrantLock();
		sufficientFunds = bankLock.newCondition();
	}

	public void transfer(int from, int to, double amount) throws Integer
	{
		bankLock.lock();
		try
		{
			while (accounts[from] < amount)
				sufficientFunds.await();
			System.out.print(Thread.currentThread());
			accounts[from] -= amount;
			System.out.printf(" %10.2f from %d to %d", amount, from, to); 
			 accounts[to] += amount; 
			 System.out.printf(" Total Balance: %10.2f%n", getTotalBalance());
			 sufficientFunds.signalAll();
		}
		finally { 
			bankLock.unlock();
		}
	}
}
```
###### Explanation:
- If the transfer method finds that sufficient funds are not available, it calls `sufficientFunds.await();`
- The current thread is now deactivated and gives up the lock. 
- This lets in another thread that can, we hope, increase the account balance.
- Once a thread calls the await method, it enters a wait set for that condition.
- The thread is not made runnable when the lock is available. Instead, it stays deactivated until another thread has called the `signalAll` method on the same condition.
- When another thread has transferred money, it should call `sufficientFunds.signalAll();`
	- This call reactivates all threads waiting for the condition. When the threads are removed from the wait set, they are again runnable and the scheduler will eventually activate them again. At that time, they will attempt to reenter the object. As soon as the lock is available, one of them will acquire the lock and continue where it left off, returning from the call to await.
- Another method, `signal` : 
	- unblocks only a single thread from the wait set, chosen at random. That is more efficient than unblocking all threads, but there is a danger. If the randomly chosen thread finds that it still cannot proceed, it becomes blocked again. If no other thread calls signal again, the system deadlocks
- When to call `signalAll` ?
	- The rule of thumb is to call signalAll whenever the state of an object changes in a way that might be advantageous to waiting threads

> Caution:
> A thread can only call await, signalAll, or signal on a condition if it owns the lock of the condition.

### Using synchronized keyword
- Every object in Java has an `intrinsic lock`.
- If a method is declared with the `synchronized` keyword, the object's lock protects the entire method.
	- That is, to call the method, a thread must acquire the intrinsic lock.
- The intrinsic object lock has **a single associated condition.**
- The `wait` method **adds a thread to the wait set**, and the `notifyAll`/`notify` methods **unblock waiting threads**.
- It is also legal to declare **static methods as synchronized**.
	- If such a method is called, it acquires the intrinsic lock of the associated **class object**. 
	- For example, if the Bank class has a static synchronized method, then the lock of the `Bank.class` object is locked when it is called. As a result, no other thread can call this or any other synchronized static method of the same class.

###### Code
```Java
	class Bank
	{
		private double[] accounts;
		public synchronized void transfer(int from,int to,int amount) throws InterruptedException
		{
			while(accounts[from] < amount)
				wait();
			accounts[from] -= amount;
			accounts[to] += amount;
			notifyAll();
		} 
	}
```

###### Explanation
- Each object has an intrinsic lock, and that the lock has an intrinsic condition. 
- The lock manages the threads that try to enter a synchronized method. The condition manages the threads that have called wait.

###### Limitations
- You cannot interrupt a thread that is trying to acquire a lock.
- You cannot specify a timeout when trying to acquire a lock.
- Having a single condition per lock can be inefficient.

###### What should you use in your code—Lock and Condition objects or synchronized methods?
- It is best to use neither Lock/Condition nor the synchronized keyword. 
- In many situations, you can use one of the mechanisms of the `java.util.concurrent package` that do all the locking for you. 
	- For example, **Blocking Queues**.
	- you will see how to use a blocking queue to synchronize threads that work on a common task later.
#### Synchronized Blocks
- There is a second mechanism for acquiring the lock: **by entering a synchronized block**
###### Syntax
```Java
	synchronized(obj)
	{
		//critical section code
	}
```
- Sometimes you will find the use of an **ad-hoc lock**.
###### Example
```Java
	class Bank
	{
		private var lock = new Object();
		...
		public void transfer()
		{
			synchronized(lock) //ad-hoc lock
			{
				...		
			}
		}
	}
```
- Here, the lock object is created only to use the lock that every Java object possesses.

#### The Monitor Concept
Locks and conditions are powerful tools for thread synchronization, but they are not very object-oriented. For many years, researchers have looked for ways to make multithreading safe without forcing programmers to think about explicit locks. One of the most successful solutions is the monitor concept.
- A monitor is a class with **only private fields**.
- Each object of that class has an associated lock.
- All methods are locked by that lock.
	- In other words, if a client calls `obj.method()`, then the lock for obj is automatically acquired at the beginning of the method call and relinquished when the method returns. 
	- Since all fields are private, this arrangement ensures that no thread can access the fields while another thread manipulates them.
- The lock can have **any number of associated conditions**.
- If a method is declared with the `synchronized` keyword, it acts like a monitor method.
- However, a Java object differs from a monitor in **three important ways :**
	1. Fields are not required to be private.
	2. Methods are not required to be synchronized.
	3. The intrinsic lock is available to clients.

#### Volatile Fields
- The `volatile` keyword offers a lock-free mechanism for ***synchronizing access to an instance field***.
- Volatile variable works only with **assignment operation**.
- If you declare a field as volatile, then the compiler and the virtual machine take into account that the field may be concurrently updated by another thread.
```Java
	private volatile boolean done; 
	public boolean isDone() { return done; } 
	public void setDone() { done = true; }
```
###### Caution
- Volatile variables **do not provide any atomicity**.
- For example, the method `public void flipDone() { done = !done; }` is not atomic 
	- It is not guaranteed to flip the value of the field. There is no guarantee that the reading, flipping, and writing is uninterrupted.

#### Final Variables
- There is one other situation in which it is safe to access a shared field—when it is declared final.
#### Atomics
- There are a number of classes in the `java.util.concurrent.atomic` package that use efficient machine-level instructions to guarantee atomicity of other operations without using locks.
- For example, the `AtomicInteger` class has methods `incrementAndGet` and `decrementAndGet` that atomically increment or decrement an integer.
```Java
	public static AtomicLong nextNumber = new AtomicLong();
	// in some thread...
	long id = nextNumber.incrementAndGet();
```
###### Explanation
- The `incrementAndGet` method atomically increments the `AtomicLong` and returns the post-increment value.
	- That is, the operations of getting the value, adding 1, setting it, and producing the new value cannot be interrupted.
	- It is guaranteed that the correct value is computed and returned, even if multiple threads access the same instance concurrently

if you want to make a more complex update, you have to use the `compareAndSet` method.
###### Example
Suppose you want to keep track of the largest value that is observed by different threads.

```Java
	public static AtomicLong largest = new AtomicLong();
	largest.updateAndGet(x -> Math.max(x,observed)); //this
	largest.accumulateAndGet(observed,Math::max); // or this
```
There are also methods `getAndUpdate` and `getAndAccumulate` that return **the old value**.

##### When to use LongAdder and LongAccumulator ?
###### LongAdder
- When you have a very large number of threads accessing the same atomic values, performance suffers because the optimistic updates require too many retries.
- A `LongAdder` is composed of multiple variables whose collective sum is the current value.
- Multiple threads can update different summands, and new summands are automatically provided when the number of threads increases.
- This is efficient in the common situation where the value of the sum is not needed until after all work has been done.
- Call `increment` to increment a counter or `add` to add a quantity, and `sum` to retrieve the total.
```Java
	var adder = new LongAdder();
	for(. . .)
		pool.submit(() -> {
			while(. . .){
				. . .
				if(. . .) adder.increment();	
			}
		});
		long total = adder.sum();
```

###### LongAccumulator
- The `LongAccumulator` generalizes this idea to an arbitrary accumulation operation.
- In the constructor, ***you provide the operation, as well as its neutral element.***
- To incorporate new values, call `accumulate`. Call `get` to obtain the current value.
```Java
	var adder = new LongAccumulator(Long::sum, 0); 
	// in some thread. . . 
	adder.accumulate(value);
```

#### DeadLock
- When a thread is currently holding some resources and needs extra resources that are being held by other threads which in turn are waiting for resources, it forms a DeadLock. 

#### Thread Local Variables
we discussed the risks of sharing variables between threads. Sometimes, you can avoid sharing by giving each thread its own instance, using the `ThreadLocal` helper class (`java.lang.ThreadLocal`).
- `T get()` : gets the current value of this thread. If get is called for the first time, the value is obtained by calling initialize.
- `void set(T t)` : sets a new value for this thread.
- `void remove()` : removes the value for this thread.
- `static <S> ThreadLocal<S> withInitial(Supplier<? extends S> supplier)` : creates a thread local variable whose initial value is produced by invoking the given supplier.
###### Example
```Java
	//To construct one instance per thread
	public static final ThreadLocal dateFormat = ThreadLocal.withInitial(() -> new SimpleDateFormat("yyyy-MMdd"));
	//To access the actual formatter,call
	string dateStamp = dateFormat.get().format(new Date());
```

# Thread-Safe Collection
- If multiple threads concurrently modify a data structure, such as a hash table, it is easy to damage that data structure.
- You can protect a shared data structure by supplying a lock, but it is usually easier to choose a thread-safe implementation instead. 

## Blocking Queues
- Many threading problems can be formulated elegantly and safely by using one or more queues.
- Producer threads insert items into the queue, and consumer threads retrieve them.
- The queue lets you safely hand over data from one thread to another.
- A blocking queue causes a thread to block when you try to add an element when the queue is currently full or to remove an element when the queue is empty.

#### Blocking Queue Methods
| Method    | Normal Action                        | Action in special circumstances                         |
| --------- | ------------------------------------ | ------------------------------------------------------- |
| `offer`   | Adds an element and returns *true*   | Returns *false* if the queue is full                    |
| `peek`    | Returns the head element             | Returns `null` if the queue is empty                    |
| `poll`    | Removes and returns the head element | Returns `null` if the queue is empty                    |
| `put`     | Adds an element                      | Blocks if the queue is full                             |
| `take`    | Removes and returns the head element | Blocks if the queue is empty                            |
| `add`     | Adds an element                      | Throws an `IllegalStateException` if the queue is full  |
| `remove`  | Removes and returns the head element | Throws a `NoSuchElementException` if the queue is empty |
| `element` | Returns the head element             | Throws a `NoSuchElementException` if the queue is empty |

## Efficient Maps, Sets, and Queues
- The` java.util.concurrent package` supplies efficient implementations for maps, sorted sets, and queues: `ConcurrentHashMap`, `ConcurrentSkipListMap`, `ConcurrentSkipListSet`, and `ConcurrentLinkedQueue`.
- These collections use sophisticated algorithms that minimize contention by allowing concurrent access to different parts of the data structure.
- Unlike most collections, the size method of these classes does not necessarily operate in constant time. Determining the current size of one of these collections usually requires traversal.
- Read more in the Core Java Volume-I Book.
# Tasks and Thread Pools
- Constructing a new thread is expensive because it involves interaction with the operating system.
- A thread pool contains a number of threads that are ready to run.
- You give a `Runnable` to the pool, and one of the threads calls the `run` method. When the `run` method exits, the thread doesn’t die but ***stays around to serve the next request***.
## Callables and Futures

- A `Runnable` encapsulates a task that runs asynchronously; you can think of it as *an asynchronous method* with *no parameters and no return value*.
- A `Callable` is similar to a `Runnable`, but it returns a value.
- The `Callable` interface is a parameterized type, with a single method `call`.

Syntax :
```Java
	public interface Callable<V>
	{
		V call() throws Exception;
	}
```

### What is a Future ?
- A `Future` holds the result of an async computation.
- It contains the following methods:
	- `V get()` : A call to this method blocks until the computation is finished.
	- `V get(long timeout, TimeUnit unit)` : This method also blocks, but it throws a `TimeoutException`, if the call timed out before the computation finished.
		- If the thread running the computation is interrupted, both `get()` methods throw an `InterruptedException`.
	- `void cancel(boolean mayInterrupt)` : This is used to cancel the computation. If the computation is currently in progress, it is interrupted if the `mayInterrupt` parameter is true.
	- `boolean isCancelled()` : 
	- `boolean isDone()` : This method returns false if the computation is still in progress, true if it is finished

### How to Execute a Callable ?
One way to execute a `Callable` is to use a `FutureTask`, which implements both the `Future` and `Runnable` interfaces, so that you can construct a thread for running it.

```Java
	Callable<Integer> task = . . .;
	var futureTask = new FutureTask<Integer>(task);
	var t = new Thread(futureTask); //it's a runnable
	t.start();
	. . .
	Integer result = task.get(); //it's a Future
```

## Executors (Unfinished)

The Executors class has a number of static factory methods for **constructing thread pools.**
#### Executor Methods
###### java.util.concurrent.Executors:
| Method                                                          | Description                                                                                                            |
| --------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `ExecutorService newCachedThreadPool()`                         | returns a cached thread pool that creates threads as needed and terminates threads that have been idle for 60 seconds. |
| `ExecutorService newFixedThreadPool(int threads)`               | returns a thread pool that uses the given number of threads to execute tasks.                                          |
| `ExecutorService newSingleThreadExecutor()  `                   | returns an executor that executes tasks sequentially in a single thread.                                               |
| `ScheduledExecutorService newScheduledThreadPool(int threads) ` | returns a thread pool that uses the given number of threads to schedule tasks.                                         |
| `ScheduledExecutorService newSingleThreadScheduledExecutor()`   | returns an executor that schedules tasks in a single thread.                                                           |
###### java.util.concurrent.ExecutorService

| Method                                   | Description                                                                                       |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------- |
| `Future submit(Callable task)`           | submits the given task for execution.                                                             |
| `Future submit(Runnable task, T result)` | returns an odd-looking `Future`. You can use such an object to call `isDone`, `cancel`, or `isCancelled`, but the `get` method simply returns null upon completion. for execution.                                                             |
| `Future submit(Runnable task)`           | yields a `Future` whose `get` method returns the given result object upon completion.                                                          |
| `void shutdown()`                        | When you are done with a thread pool, call `shutdown`. This method initiates the shutdown sequence for the pool. An executor that is shut down accepts no new tasks. When all tasks are finished, the threads in the pool die. Alternatively, you can call `shutdownNow()`. The pool then cancels all tasks that have not yet begun. |

###### java.util.concurrent.ThreadPoolExecutor
| Method                   | Description |
| ------------------------ | ----------- |
| `int getLargestPoolSize()` |   returns the largest size of the thread pool during the life of this executor.          |

###### java.util.concurrent.ScheduledExecutorService
| Method                                                                                                | Description                                                                                           |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| `ScheduledFuture schedule(Callable task, long time, TimeUnit unit)`                                   | schedules the given task after the given time has elapsed.                                            |
| `ScheduledFuture schedule(Runnable task, long time, TimeUnit unit)`                                   | schedules the given task after the given time has elapsed.                                            |
| `ScheduledFuture scheduleAtFixedRate(Runnable task, long initialDelay, long period, TimeUnit unit)`   | schedules the given task to run periodically, every period units, after the initial delay has elapsed |
| `ScheduledFuture scheduleWithFixedDelay(Runnable task, long initialDelay, long delay, TimeUnit unit)` |     schedules the given task to run periodically, with delay units between completion of one invocation and the start of the next, after the initial delay has elapsed.                                                                                                  |

##### Detailed Explanation of the methods
- The `newCachedThreadPool` method constructs a thread pool that executes each task immediately, using an existing idle thread when available and creating a new thread otherwise.
- The `newFixedThreadPool` method constructs a thread pool with a fixed size. If more tasks are submitted than there are idle threads, the un-served tasks are placed on a queue. They are run when other tasks have completed.
- The `newSingleThreadExecutor` is a degenerate pool of ***size 1*** where a single thread executes the submitted tasks, one after another. 
 These three methods return an object of the `ThreadPoolExecutor` class that implements the `ExecutorService` interface.
 ##### When to use what ?
 - Use a cached thread pool when you have threads that are short-lived or spend a lot of time blocking.
 - However, if you have threads that are working hard without blocking, you don’t want to run a large number of them together
 - For optimum speed, the number of concurrent threads is the number of processor cores. In such a situation, you should use a fixed thread pool that bounds the total number of concurrent threads.
 - The single-thread executor is useful for performance analysis. If you temporarily replace a cached or fixed thread pool with a single-thread pool, you can measure how much slower your application runs without the benefit of concurrency.
#### How to use a Thread pool ?
1. Call the static `newCachedThreadPool` or `newFixedThreadPool` method of the Executors class. 
2. Call `submit` to submit `Callable` or `Runnable` objects.
3. Hang on to the returned `Future` objects so that you can get the results or cancel the tasks.
4. Call `shutdown` when you no longer want to submit any tasks.

#### Controlling Groups of Tasks (Unfinished)

Sometimes, an executor is used for a more tactical reason—simply to control a group of related tasks.

#### The Fork-Join Framework (Unfinished)

- Some applications use a large number of threads that are mostly idle. An example would be a web server that uses one thread per connection. 
- Other applications use one thread per processor core, in order to carry out computationally intensive tasks, such as image or video processing.
- The fork join framework, which appeared in Java 7, is designed to support the latter
```Java
	if (problemSize < threshold)
		//solve problem directly
	else
	{
		//break problem into subproblems
		//recursively solve each subproblem
		//combine the results
	}
```
# Asynchronous Computation (Pending)
