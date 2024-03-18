---
type:
  - Chapter
tags:
  - Java
  - Exception
  - Assertion
  - Debugging
  - IDE
published: true
created: 2023-12-27 20:16
modified: 2024-01-02T09:41:00
folder: Core Java
---
# The classification of Exceptions

>[!quote]
>*"If it is a RuntimeException, it was your fault"*

>[!info]
>Exceptions that inherit from *RuntimeException* include such problem as:
>- A bad cast
>- An out-of-bounds array access
>- A null pointer access
>
>Exceptions that do not inherit from *RuntimeException* include:
>- Trying to read past the end of a file
>- Trying to open a file that doesn't exist
>- Trying to find a *Class* object for a string that does not denote an existing class

# Declaring checked exceptions

>[!info]
>Any exception that derives from the class *Error* or the class *RuntimeException* is an unchecked exception.

>[!info]
>The place in which you advertise to the compiler that your method can throw an exception is the header of the method.
>```java
>public FileInputStream(String name) throws FileNotFoundException

If *FileNotFoundException* object is thrown, the runtime system will search for an exception handler that knows how to deal with this object.

>[!note]
>You don't have to advertise exceptions in every methods. You can just advertise it in the following four situations:
>1. You call a method that throws a checked exception
>2. You detect a error and throw a checked exception
>3. You make a programming error that gives rise to an unchecked exception
>4. An internal error occurs in the virtual machine or runtime library

>[!warning]
>*Subclass methods's exceptions cannot be more general than those of superclass methods. If the superclass method throws no checked exception at all, neither can the subclass*

# Creating exception classes

>[!note]
>*To create  your own class, just derive it from Exception or from a child of it. It is customary to give both a default constructor and a constructor that contains a detailed message*

# Catching an exception

>[!info]
>If an exception occurs that is not caught, the program will terminate and print message to the console, giving the type of the exception and stack trace

>[!note]
>If any code inside *try* block throws an exception then:
>1. The program skips the remainder of the code in the *try* block
>2.  The program executes the handler code insider the *catch* clause
>
>If none of the code in the *try* block throws an exception, then the program skip the *catch* clause

# The finally clause

>[!info]
>The code in the *finally* clause executes whether or not an exception was caught.

>[!warning]
>A *finally* clause can yield unexpected results when it contains *return* statements. Suppose you exit the middle of a *try* block with a *return* statement. Before the method returns, the *finally* block is executed. If the *finally* block also contains a *return* statement, then it masks the original return value.
>The body of the *finally* clause is intended for cleaning up resources. Don't put statements that change the control flow (*return, throw, break, continue*) inside a *finally* clause.

```java
public static int parseInt(String s) {
	try {
		return Integer.parseInt(s);
	}
	finally {
		return 0;   // ERROR
	}
}

// In this example, parseInt method will always return 0 value before the expected value from param. In worst case, try block throw an exception but it is masked by the 0 value.
```

# The try-with-resources statement

As of Java 7, there is a useful shortcut to the code pattern:

```java
// opne a resource
try {
	// work with the resource
}
finally {
	// close the resource
}
```

provided the resource belongs to a class that implements the *AutoCloseable* interface. That interface has a single method *close()*

In the simplest variant, the try-with-resources statement has the form
```java
try (Resourse res = ...) {
	// work with res
}
```

when the *try* block exits, then *res.close()* is called automatically.  You can specify multiple resources in the *try* parenthesis.

>[!note]
>A try-with-resources statement can itself have *catch* clause and *finally* clause. These are executed after closing the resources.

# Analyzing stack trace elements

>[!info]
>A *stack trace* is a listing of all pending method calls at a particular point in the execution of a program. They are displayed whenever a program terminates with an uncaught exception

>[!example]
>```
>factorial(3):
stackTrace.StackTraceTest.factorial(StackTraceTest.java:20)
stackTrace.StackTraceTest.main(StackTraceTest.java:36)factorial
(2):
stackTrace.StackTraceTest.factorial(StackTraceTest.java:20)
stackTrace.StackTraceTest.factorial(StackTraceTest.java:26)
stackTrace.StackTraceTest.main(StackTraceTest.java:36)
factorial(1):
stackTrace.StackTraceTest.factorial(StackTraceTest.java:20)
stackTrace.StackTraceTest.factorial(StackTraceTest.java:26)
stackTrace.StackTraceTest.factorial(StackTraceTest.java:26)
stackTrace.StackTraceTest.main(StackTraceTest.java:36)
return 1
return 2
return 6

# Tips for using exceptions

>[!tips]
>1.* Exception handling is not supposed to replace a simple test*
>2. *Do not micromanage exceptions*
>3. *Make good use of the exception hierarchy*: find an appropriate subclass of *Exception* or create your own
>4. *Do not squelch exceptions*
>5. *When you detect an error, "tough love" works better than indulgence*
>6. *Propagating exceptions is not a sign of shame*
>7. *Use standard methods for reporting null-pointer and out-of-bounds exceptions*: *requireNonNull, checkIndex, checkFromToIndex, checkFromIndexSize*
>8. *Don't show stack traces to end users*: you can be attacked


# Assertion concept

>[!info]
>Assertions are a commonly used idiom of defensive programming (double check). 

You can use exceptions to test the program. But if you have lots of checks, the program may run quite a bit slower than it should.

The assertion mechanism allows you to check during testing and to have them automatically removed in the production code. There are two form:

```java
assert x >= 0;   // assert that x is non-negative

// and

assert x >= 0 : x;   // the same but the value of x can be displayed later
```

# Assertion enabling and disabling

>[!note]
>*By default, assertions are disabled. Enable them by running the program with the -enableassertions or -ea option*. You don't have to recompile to enable/disable it
>```
>java -enableassertions MyApp

You can also enable it in specific classes or in entire packages:
```bash
java -ea:MyClass -ea:com.mycompany.mylib MyApp
```

# Using assertions for parameter checking

>[!note]
>When should you choose assertions? Keep these points in mind:
>- Assertion failures are intended to be fatal, unrecoverable errors.
>- Assertion checks are turned on only during development and testing

You would not use it for signaling recoverable conditions to another part of the program or for communicating problems to the program user.

>[!note]
>You should **strictly** follow the guide in method documentations. 

# Logger

>[!tip]
>A logger that is not referenced by any variable can be garbage-collected. To prevent this, save a reference to the logger with a static variable.

## A logging recipe

>[!tips]
>1. For a simple application, choose a single logger. It is a good idea to give the logger the same name as your main application package.
>2. The default logging configuration logs all messages of level *INFO* or higher to the console. 
>3. Whenever you are tempted to call *System.out.println*, emit a log message instead.

# Debugging tips

>[!tips]
>Here is some tips that may be worth trying before you launch the debugger in IDE:
>1. You can log the value of variables 
>2. You can put a separate *main* method in each class to test it in isolation
>3. Use *JUnit* for testing
>4. You can get a stack trace from any exception object with the *printStackTrace* method in the *Throwable* class.
>5. You can trap error stream as: java MyProgram 2 > errors.txt
>6. You want to log uncaught exceptions to a log file:
>>[!example]
>>```
>>Thread.setDefaultUncaughtExceptionHandler (
>>	new Thread.UncaughtExceptionHandler() {
>>			public void uncaughtException(Thread t, Throwable e) {
>>				// save to log file	
>>			};
>>	}
>>);
>
>9. To watch class loading, launch the JVM with the -verbose flag. This can help to diagnose class path problems
>10. The -Xlint option tells the compiler to spot common code problems (e.g. missing *break* in *switch*)
>11. JVM has support for *monitoring* and *management* of Java apps, allowing the installation of agents in the virtual machine that track memory consumption, thread usage, class loading. JDK ships with a graphical tool called *jconsole* that display stats about the performance
>12. *Java Mission Control* is a professional-level profiling and diagnostics tool.


