---
type:
  - Chapter
tags:
  - Java
  - Inheritance
  - Polymorphism
  - Method
published: true
created: 2023-12-27 09:53
modified: 2023-12-27T17:03:00
folder: Core Java
---
# Overriding methods

>[!info]
>*super* is not a reference to an object. You cannot assign the value super to another object variable. It's just a special keyword that directs the compiler to invoke superclass methods

>[!info]
>Automatically selecting the appropriate method at runtime is called *dynamic binding*

# Inheritance hierarchies

>[!note]
>*Java does not support multiple inheritance*

# Polymorphism

>[!note]
>*The "is-a" rule states that every object of the subclass is an object of the superclass*


>[!warning]
>*In this case, staff[0] and boss refer to the same object. However, staff[0] is considered to be only an Employee object by the compiler*
>
>>[!example]
>>```java
>>Manager boss = new Manager(...);
>>Employee[] staff = new Employee[3];
>>staff[0] = boss;
>

That means you can call:

```java
boss.setBonus(5000);
```

but you cannot call:

```java
staff[0].setBonus(5000);   //setBonus doesn't exist in Employee class
```

>[!warning]
>*Arrays of subclass references can be converted to arrays of superclass references without a cast*
>
>>[!example]
>```java
>Manager[] managers = new Manager[10];
>
>// It is legal to convert this array
>Employee[] staff = managers;

# Understanding method calls

>[!info]
>x.f(param)
>
>Here is what happens:
>1. The compiler looks at the declared type of the object and the method name, enumerates all the methods have that name in that class and superclass
>2. Overloading resolution
>3. If the method is *private, static, final* or a constructor, then the compiler knows exactly which method to call. This is called *static binding*
>4. In *dynamic binding*, the VM must call the version of the method that is appropriate for the **actual** type of the object. Let's call the actual type is D, a subclass of C. If the class D defines that method, it is called. If not D's superclass is searched and so on. 

# Preventing inheritance: Final Classes and Methods

>[!info]
>If you want to prevent forming a subclass of one of your classes, put the *final* keyword in the definition of that class.
>>[!example]
>>```java
>>public final class Executive extends Manager {...}

You can also make this to methods to prevent subclass overriding it. All methods in a final class are automatically *final*, except *final* fields.

# Pattern matching for *instanceof*

You can replace this code:
```java
if (staff[i] instanceof Manager)
{
   Manager boss = (Manager) staff[i];
   boss.setBonus(5000);
}
```

by using this:
```java
if (staff[i] instanceof Manager boss)
{
    boss.setBonus(5000);
}
```

# Protected access

>[!note]
>*In Java, a protected field is accessible by any class in the same package.*

# Object: The Cosmic Superclass

>[!info]
>The *Object* class is the ultimate ancestor - every class in Java extends *Object*

You can use *Object* variable to refer to objects of any type:
```java
Object obj = new Employee("Harry Hacker", 35000);
```

>[!note]
>*All array types, no matter whether they are arrays of objects or arrays of primitive types, are class types that extends the Object class*

## The *equals* method

>[!info]
>You can implement *equals* method to test whether one object is considered equal to another

>[!example] This is recipe for writing the perfect *equals* method:
>
>```java
>public class Employee
{
.  . .
public boolean equals(Object otherObject)
{
// a quick test to see if the objects are identical
   if (this == otherObject) return true;
// must return false if the explicit parameter is null
if (otherObject == null) return false;
// if the classes don't match, they can't be equal
if (getClass() != otherObject.getClass())
return false;
// now we know otherObject is a non-null Employee
Employee other = (Employee) otherObject;
// test whether the fields have identical values
return name.equals(other.name) && salary == other.salary && hireDay.equals(other.hireDay);
}
}

>[!tip]
>To guard against the possibility that *name* or *hireday* are *null*, use the *Objects.equals* method. If you redefine *equals* in a subclass, include a call *super.equals(other)*

# Hashcode

>[!tip]
>If you have ﬁelds of an array type, you can use the static Arrays.hashCode
method to compute a hash code composed of the hash codes of the array
elements.

# ToString

>[!example]
>```java
>public String toString()
{
return getClass().getName()
+"[name=" + name
+",salary=" + salary
+",hireDay=" + hireDay
 "]";
}

>[!tip]
>You should implement *toString* method in each class you write.It's useful for logging purpose

# Ensure capacity for ArrayList

>[!example]
>```java
>staff.ensureCapacity(100);   // the first 100 calls to add will not involve any costly reallocation

>[!tip]
>You can use *trimToSize* method to adjust the **size** of the memory block to use exactly as much storage space as is required to hold the current number of elements. The garbage collector will reclaim any excess memory.

>[!warning]
>A *ArrayList\<Integer\>* is far less efficient than an *int[]*. You would only want to use this for small collections

>[!warning]
>*You should always call equals method when comparing wrapper objects (Integer, Boolean, Double, ...)*

>[!warning]
>*You cannot use wrapper class to modify parameters because wrapper classes are immutable*
>```java
>public static void triple (Integer x)   // won't work
>{}

# Methods with a variable number of parameters

>[!example]
>```java
>public class PrintStream
{
public PrintStream printf(String fmt, Object... args)
{return format(fmt, args);
}
}

You can define your own method like this:

>[!example]
>```
>public static double max(double... values)
{
   double largest = Double.NEGATIVE_INFINITY;
   for (double v : values) if (v > largest) largest = v;
   return largest;
}

# Abstract class

>[!tip]
>Some programmers don’t realize that abstract classes can have concrete methods. You should always move common ﬁelds and methods (whether abstract or not) to the superclass (whether abstract or not).
>>[!example]
>>```
>>public abstract class Person
{
private String name;
public Person(String name)
{
this.name = name;
}
public abstract String getDescription();
public String getName()
{
return name;
}
}
>>```

>[!note]
>You cannot create an abstract object. If a class has one abstract method it will be tagged as abstract as well.
>


