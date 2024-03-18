---
type:
  - Chapter
tags:
  - Java
  - Interface
  - Lambda
published: true
created: 2023-12-27 17:05
modified: 2023-12-27T20:13:00
folder: Core Java
---
# Static methods

>[!info]
>You can place static methods inside an interface.
>>[!example]
>>```
>>public interface Path
{
public static Path of(URI uri) { . . . }
public static Path of(String first, String... more) { . . . }
. . .
}

# Callback


>[!info]
>When you construct a timer, you set the time interval and tell it what it should do whenever the time interval has elapsed. In many other languages, you supply function the time should call periodically. 
>However Java take the object approach. The timer then calls methods of that object which implemented from a specific interface.

# Lambda expression

>[!info]
>You can supply a lambda expression whenever an object of an interface with a single abstract method is expected. Such an interface is called a functional interface

>[!example]
>```
>Arrays.sort(words,
(first, second) -> first.length() - second.length());

(first, second) -> first.length() - second.length()); is similar to an object of a class which has implement the desired method, in this case is *compare* method of *Comparator* interface.

# Processing Lambda expressions

>[!info]
>These are some reasons for executing a block of code (as lambda) later:
>- Running the code in a separate thread
>- Running the code multiple times
>- Running the code at the right point in an algorithm
>- Running the code when something happens
>- Running the code only when neccessary


For example:
```java
repeat(10, () -> System.out.println("Hello"));

// To accept lambda, we need to pick a functional interfaces (in this example is Runnable interface):

public static void repeat(int n, Runnable action) {
	for (int i = 0; i < n; i++) action.run();
}
```

# Inner class

>[!info]
>There are two reasons to define an inner class:
>- Inner classes can be hidden from other classes in the same package
>- Inner class methods can access the data from the scope in which they are defined - including the data that would otherwise be private

