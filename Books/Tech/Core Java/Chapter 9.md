---
type:
  - Chapter
tags:
  - Java
  - Collections
  - Algorithm
published: true
created: 2024-01-15 23:33
modified: 2024-01-19T10:34:00
folder: Core Java
---
# Iterators

```java
public interface Iterator<E> {
	E next();
	boolean hasNext();
	void remove();
	default void forEachRemaining(Consumer<? super E> action);
}
```

>[!note]
>The for-each loop works with any object that implements the *Iterable* interface. *Collection* interface extends this interface

You can use *forEachRemaining* instead of a loop:
```java
iterator.forEachRemaining(element -> do something);
```
The java collections framework defines a number of interfaces for different types of collections:

![Imgur](https://i.imgur.com/ftPJ5kh.png)

# Maps

>[!note]
>You can use *forEach* to iterate over the keys and values of a map
>>[!example]
>>```
>>scores.forEach((k, v) -> System.out.println(k + " " + v));

If you want to update value, include in the first time:

```java
counts.put(word, counts.getOrDefault(word, 0) + 1);
// or
counts.putIfAbsent(word, 0);
// or 
counts.merge(word, 1, Integer::sum);
```

## Map views

>[!info]
>There are three views:
>- Set\<K\> keySet()     // this is not HashSet or TreeSet
>- Collection\<V\> values()
>- Set\<Map.Entry\<K, V\>\> entrySet()

## Linked hash sets and maps

>[!info]
>*LinkedHashSet* and *LinkedHashMap* classes remember in which order you inserted items using a doubly linked list


>[!info]
>A linked hash map can use access order to iterate elements. 

```java
LinkedHashMap<K, V>(initialCapacity, loadFactor, true)
```

## Enumeration sets and maps

**Enumeration sets**
```java
enum Weekday { MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY,
SATURDAY, SUNDAY };
EnumSet<Weekday> always = EnumSet.allOf(Weekday.class);
EnumSet<Weekday> never = EnumSet.noneOf(Weekday.class);
EnumSet<Weekday> workday = EnumSet.range(Weekday.MONDAY,
Weekday.FRIDAY);
EnumSet<Weekday> mwf = EnumSet.of(Weekday.MONDAY,
Weekday.WEDNESDAY, Weekday.FRIDAY);
```

**Enumeration maps**

```java
var personInCharge = new EnumMap<Weekday, Employee>(Weekday.class);
```

>[!note]
>*of* methods are unmodifiable. 

## Subranges

>[!info]
>You can use *subList* method to get a sublist.

## Synchronized views

>[!info]
>You can use *synchronizedMap* method to turn any map to a synchronized map and use it in many threads

```java
var map = Collections.synchronizedMap(new HashMap<String, Employee>());
```

## Convert Collections and Arrays

```java
String[] names = ...;
List<String> staff = List.of(names);

Object[] names = staff.toArray();   // cannot use cast

String[] values = staff.toArray(String[]::new);   // pass an array constructor
```
