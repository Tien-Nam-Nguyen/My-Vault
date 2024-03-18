---
type:
  - Chapter
tags:
  - Java
  - OOP
published: true
created: 2023-12-25 09:16
modified: 2023-12-25T18:39:00
folder: Core Java
---
# Object variables

```java
Date rightNow = new Date();
Date startTime;
startTime = rightNow;   // REFER to the same object on heap
```

You can think of Java object variables as analogous to object pointers in C++.

![Imgur](https://i.imgur.com/VFZJTBC.png)

>[!info]
>All Java objects live on the heap. When an object contains another object variable, it contains just a pointer to another heap object


>[!warning]
>*Getter methods should not return references to mutable objects. It will break encapsulation. As a rule of thumb, always use clone method whenever you need to return a copy of a mutable field*

# Final field

>[!info]
>Final fields must be initialized when the object is constructed. Use final for mutable class can be confusing (final means referred object can't be changed, but the value can still be mutated)

# Static

>[!info]
>Static methods don't operate on individual objects (it don't contain *this* keyword)


# Main method
>[!info]
> Every class can have a *main* method. To demo, simply execute that class file. If you want to run whole application, call *main* method in the Application class file and other *main* method will not be executed
# Method parameters

>[!note]
>*Java always use call by value (copy value of the outside variable to the parameter of that method). If the parameters is object variable, the values it copy are the object references (pointer)*
# Default field initialization

>[!info]
>If you don't set, it is automatically set to a default value: numbers to 0, boolean to false and object references to null.
# Record

>[!info]
>Record in Java is a special form of a class whose state is immutable and readable by the public

```java
public record Point(double x, double y) {}

// It is the same as
class Point {
	private final double x;
	private final double y;
}

// How to use ?
Point p = new Point(1.1, 2.2);
System.out.println(p.x());    // x() method is automatically generated
System.out.println(p.y());

```
# Packages

>[!info]
>A class can use all classes from it own package and all *public* classes from other packages

# JAR file

>[!note]
>*A JAR (Java archive) file contains multiple class files and subdirectories in a compressed format. You can use ZIP utility to peek inside JAR files*

```bash
jar [options] file1 file2   // compress files

java -jar MyProgram.jar   // run jar file
```

# Documentation comments

>[!info]
>A comment starts with a /\*\* and ends with a \*/. Each of this documentation comments contains free-form text followed by tags. A tags starts with an @, such as @since or @param. The first sentence of the free-form text should be a summary statement. You can use HTML such as:
>-  <\em>: emphasis
>- <\strong>: strong emphasis
>- <\ul>: bulleted list
>- <\img>: image. 
>Use {@code ...} for code.

If your comments links to other files such as images, place those files into a subdirectory, named *doc-files*.

## Class comments

>[!note]
>*Placed after import statements and before class definition*

```java
/**
* A {@code Card} object represents a playing card, such
* as "Queen of Hearts". A card has a suit (Diamond, Heart,
* Spade or Club) and a value (1 = Ace, 2 . . . 10, 11 = Jack,
* 12 = Queen, 13 = King)
*/
public class Card
{
. . .
}
```

## Method comments

>[!note]
>*Placed before the method that it describe*

```java
/**
* Raises the salary of an employee.
* @param byPercent the percentage by which to raise the
salary (e.g., 10 means 10%)
* @return the amount of the raise
*/
public double raiseSalary(double byPercent)
{
	double raise = salary * byPercent / 100;
	salary += raise;
	return raise;
}
```

## Field comments

>[!note]
>*You only need to document public fields -- that means static constants*

```java
/**
* The "Hearts" card suit
*/
public static final int HEARTS = 1;
```

 