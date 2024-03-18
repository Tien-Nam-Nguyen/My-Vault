---
type:
  - Chapter
tags:
  - Java
  - Generic
published: true
created: 2024-01-02 09:41
modified: 2024-01-02T11:52:00
folder: Core Java
---
# Why Generic Programming?

>[!info]
>*Generic programming* means writing code that can be reused for objects of many different types.
# Defining a simple generic class

```java
public class Pair<T>
{
	private T first;
	private T second;
	public Pair() { first = null; second = null; }
	public Pair(T first, T second) { this.first = first; this.second = second; }
	public T getFirst() { return first; }
	public T getSecond() { return second; }
	public void setFirst(T newValue) { first = newValue; }
	public void setSecond(T newValue) { second = newValue; }
}
```

>[!note] Common practice
>The Java library uses the variable E for element type of a collection, K and V for key and value of a table, and T for "any type at all"

# Generic methods

You can also define a generic method inside an ordinary class:
```java
class ArrayAlg
{
	public static <T> T getMiddle(T... a)
	{
		return a[a.length / 2];
	}
}
```

You can call it like this:
```java
String middle = ArrayAlg.<String>getMiddel("John", "Q.", "Public");

// or like this when compiler can automatically infer String from arguments
String middle = ArrayAlg.getMiddel("John", "Q.", "Public");
```

Consider this example:
```java
double middle = ArrayAlg.getMiddle(3.14, 1729, 0);
```

The compiler autoboxed parameters into *Double* and *Integer*, then it tried to find a common supertype of these classes. It found two: *Number* and *Comparable*. Then error message complains that there are two ways of interpreting this code.

# Bounds for Type variables

```java
class ArrayAlg
{
	public static <T> T min(T[] a) // almost correct
	{
		if (a == null || a.length == 0) return null;
		T smallest = a[0];
		for (int i = 1; i < a.length; i++)
		if (smallest.compareTo(a[i]) > 0) smallest = a[i];
	return smallest;
	}
}
```

What if *smallest* doesn't have *compareTo* method? You can restrict T to a class that implements *Comparable* interface:
```java
public static <T extends Comparable> T min(T[] a) ...
```

You can have multiple bounds as interface, but at most one of the bounds can be a class:
```java
T extends Comparable & Serializable
```

# Type erasure

When you define a generic type, a corresponding raw type is automatically provided. The type variables are erased and replaced by their bounding types (*Object* for variables without bounds)

```java
public class Pair
{
	private Object first;
	private Object second;
	public Pair(Object first, Object second) { this.first = first; this.second = second; }
	public Object getFirst() { return first; }
	public Object getSecond() { return second; }
	public void setFirst(Object newValue) { first = newValue; }
	public void setSecond(Object newValue) { second = newValue; }
}
```

If user defines multiple bounds, the first bound will be selected:
```java
public class Interval<T extends Comparable & Serializable> implements Serializable
{
	private T lower;
	private T upper;
	. . .
	public Interval(T first, T second)
	{
		if (first.compareTo(second) <= 0) { lower = first; upper
		= second; }
		else { lower = second; upper = first; }
	}
}
```

turn into:
```java
public class Interval implements Serializable
{
	private Comparable lower;
	private Comparable upper;
	. . .
	public Interval(Comparable first, Comparable second) { . . .
	}
}
```

# Translating generic expressions

>[!note]
>When you program a call to a generic method, the compiler inserts casts when the return type has been erased. The compiler translate the method call into two virtual machine instruction:
>1. A call to a raw method to get *Object*
>2. A cast of the returned *Object* to the type *Employee*

>[!note]
>The type erasure interferes with polymorphism. To fix this, the compiler generates a bridge method in subclass which is the same as in superclass, but in the body it calls the real method in subclass having a more specific type parameters.

# Restrictions and limitations

>[!note]
>1. Type parameters cannot be instantiated with primitive types
>2. Runtime type inquiry only works with raw types (*instanceof* call)
>3. You cannot create arrays of parameterized types
>4. Varagrs warnings appear if you use T...
>5. You cannot instantiate *new T()* or *new T[n]*
>6. You cannot throw or catch instances of a generic class

# Inheritance rules

>[!note]
>There is no relationship between Pair\<S\> and Pair\<T\>, no matter how S and T are related
>![Imgur](https://i.imgur.com/ffRNiDa.png)

>[!note]
>Generic classes can extend or implement other generic classes. In this regard, there are no different from ordinary classes.
>![Imgur](https://i.imgur.com/SVCspOr.png)

