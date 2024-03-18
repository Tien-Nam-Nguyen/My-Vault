---
type:
  - Chapter
tags:
  - Java
  - Concurrency
  - Asynchronous
  - Thread
published: true
created: 2024-01-20 09:19
modified: 2024-01-25T22:58:00
folder: Core Java
---

# What are threads?

>[!info]
>You can create a thread by implementing *Runnable* interface and pass it as an argument in *Thread* constructor. Start the thread by *start* method.

```java
public interface Runnable {
	void run();
}

// or 

Runnable r = () -> {
	// code
};

// contruct a thread
var t = new Thread(r);

// start the thread
t.start();
```

>[!caution]
>Do not call *run* method of *Thread* or *Runnable* object. It directly executes the task in the same thread, no new thread is started.

# Thread states

>[!info]
>Threads can be in one of six state:
>- New
>- Runnable
>- Blocked
>- Waiting
>- Timed waiting
>- Terminated


![Imgur](https://i.imgur.com/uP5CRnQ.png)o

# Daemon threads

>[!info]
>Daemon threads are threads that has no other roles in life than to serve others (e.g. timer, clean up threads,...). When only daemon threads remain, the virtual machine exits

# Thread priorities

>[!info]
>Evert thread has a priority. By default, a thread inherits the priority of the thread that constructed it. You can increase or decrease the priority with the *setPriority* method. The Java thread priorities must be mapped to the priority levels of the host platform.


>[!note]
>The *reentrant* lock is used in class to protect the resources. A thread can acquire a lock it already owns several times. The thread has to call *unclock* for every call to *lock* in order to relinquish the lock

# Condition object

>[!note]
>Condition object is used to mange threads that have acquired a lock but cannot do useful work because it do not fulfil condition of condition object.

We don't want to transfer money if the account don't have enough money:

```java
// You should not use this
if (bank.getBalance(from) >= amount)
	// thread might be deactivated at this point, when it return to continue, the above condition may have been not true anymore
	bank.transfer(from, to, amount);
```

A lock object can have one or more associated condition objects:

```java
class Bank {
	private Condition sufficientFunds;
	private Lock bankLock = new ReentrantLock();
	. . .
	public Bank() {
		. . .
		sufficientFunds = bankLock.newCondition();
	}
}
```

If the *transfer* method find that sufficient funds are not available, it calls

```java
sufficientFunds.await();
```

The current thread is now deactivated, go to wait set and gives up the lock. This lets in another thread that can increase the account balance.

When another thread has transferred money, it should call

```java
sufficientFunds.signalAll();
```

This call reactivates all threads waiting for the condition. When the threads are removed from the wait set, they are again runnable and the scheduler will eventually activate them again. 

>[!note]
>In general, a call to *await* should be inside a loop of the form:
>```java
>while (!(OK to proceed))
>	condition.await();

>[!note]
>If no thread call signal, all *await* thread will never run again (deadlock)

# Synchronized keyword

>[!info]
>If a method is declared with the *synchronized* keyword, an intrinsic lock of it will protect the entire method.

The *wait, notifyAll, nofity* methods are final methods of the *Object* class is equivalent to *await, signalAll* respectively.

```java
class Bank
{
	private double[] accounts;
	public synchronized void transfer(int from, int to, int amount) throws InterruptedException
{
	while (accounts[from] < amount)
		wait(); // wait on intrinsic object lock's single condition
		accounts[from] -= amount;
		accounts[to] += amount;
		notifyAll(); // notify all threads waiting on the condition
}
	public synchronized double getTotalBalance()
	{
	. . .
	}
}
```

# Volatile keyword

>[!info]
>If you declared a filed as *volatile*, then the compiler and the virtual machine take into account that the field may be concurrently updated by another thread.

A change to *done* in one thread is visible from any other thread that reads *done*

```java
private volatile boolean done;
public boolean isDone() {return done;}
public void setDone() {done = true;}
```

# Thread-safe collections

>[!info]
>Some thread-safe collections:
>- *BlockingQueue*
>- *ConcurrentHashMap*
>- *ConcurrentSkipListMap*
>- *ConcurrentSkipListSet*
>- *ConcurrentLinkedQueue*
>

# Process

Building a process:

```java
var builder = new ProcessBuilder("gcc", "myapp.c");
```

Running a process: after you configured the builder, invoke its *start* method to start the process

```java
Process process = new ProcessBuilder("/bin/ls", "-l")
.directory(Path.of("/tmp").toFile())
.start();
try (var in = new Scanner(process.getInputStream()))
{
	while (in.hasNextLine())
		System.out.println(in.nextLine());
}
```
