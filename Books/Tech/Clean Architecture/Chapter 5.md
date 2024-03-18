---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - OOP
published: true
created: 2023-11-16 15:59
modified: 2023-11-16T17:28:00
folder: Tech
---
>[!question] What is OO?
>*The combination of data and function*

Is OO really a mixture of *encapsulation, inheritance* and *polymorphism*
# Encapsulation?

In C++, the users of header files can still know about members of that class. Java and C# simply abolished header/implementation split altogether, thereby weakening encapsulation even more.

For these reason, it is difficult to accept that OO depends on strong encapsulation.

# Inheritance?

Before OOP, C can do a simple inheritance by casting type with the same order fields. Languages nowadays make it more convenient to do inherit.

# Polymorphism?

OO languages eliminate all the complex convention of old polymorphism which using function pointers, therefore OO languages make polymorphism trivial.

# The power of Polymorphism

We can use polymorphism to make our programs independent and prevent rewriting portions of the original program.

# Dependency inversion

Source code dependency: 

![Imgur](https://i.imgur.com/yc6X4AV.png)

But when polymorphism is brought into play, however, something very different can happen:

![Imgur](https://i.imgur.com/ZAsZ08c.png)

>[!note]
>Any source code dependency, no matter where it is, can be inverted

