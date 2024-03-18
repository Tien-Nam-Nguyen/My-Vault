---
type:
  - Chapter
tags:
  - Java
  - Structures
published: true
created: 2023-12-24 21:29
modified: 2023-12-24T23:25:00
folder: Core Java
---
# Conversion between types

![Imgur](https://i.imgur.com/Q3SD8Fd.png)

Dotted arrows denote that conversion can cause loss precision.

# Assignment

x += 3.5

if x is int then it equivalent to x = (int)(x + 3.5).

# Switch

```java
String seasonName = switch (seasonCode) 
{
	case 0 -> "Spring";
	case 1 -> "Summer";
	case 2 -> "Fall";
	case 3 -> "Winter";
	default -> "???";
};
```

>[!note]
>*The above example does not have fallthrough behavior. But if "->" is replaced by ":" then it would have fallthrough. If you want to include statements in case without fallthrough, use braces with yield keyword*

# StringBuilder

Concatenate strings into a longer string using "+" can be inefficient and waste memory. Use *StringBuilder* instead.

```java
StringBuilder builder = new StringBuilder();
builder.append("hello");
builder.append(" ");
builder.append("world");
```

# Reading input

To read console input, construct *Scanner*:

```java
import java.util.*;
Scanner in = new Scanner(System.in);

// Read a line 
String aLine = in.nextLine();

// Read a word
String firstName = in.next();

//Read a integer
int age = in.nextInt();

...
```

>[!note]
>*Whenever you use a class that is not defined in java.lang, you need to use import*

# Formatting output

```java
double x = 123.456789;
System.out.printf("%8.2f", x); // __123.46

// 8: minimum width
// 2: numbers of digit after ".".
```

# Big numbers

```java
// Turn ordinary number to big number
BigInteger a = BigInteger.valueOf(100);

// For longer numbers
BigInteger reallyBig = new BigInteger("123456789987654321123456789");
```

# Array copying

```java
int[] luckyNumbers = smallPrimes;
luckyNumbers[5] = 12; // now smallPrimes is also 12

// How to really copy 
int[] copiedLuckyNumbers = Arrays.copyOf(luckyNumbers, luckyNumbers.length);
```