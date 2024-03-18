---
type:
  - Chapter
tags:
  - Java
  - Introduction
published: true
created: 2023-12-23 11:34
modified: 2023-12-23T12:16:00
folder: Core Java
---
# Compilation and execution

![][https://media.geeksforgeeks.org/wp-content/uploads/java.jpg]

# Portable

>[!note]
>*Unlike C and C++, the size of primitive data types are specified, as is the behavior of arithmetic on them. Java does a great job of letting developer work in a platform-independent manner, so you don't have to worry about underlying operating system*

# Interpreted

>[!info]
>The Java interpreter can execute Java bytecodes directly on any machine to which the interpreter has been ported. Since linking is a more incremental and lightweight process, the development process can be much more rapid and exploratory

>[!note]
>*Java doesn't have linker as C, it use dynamic linking. The class loader loads the main class (.class) into memory. All other classes referenced in the program are loaded too.*

>[!info]
> Java interpreter is a part of JRE (Java Runtime Environment). JRE contains JVM, Java interpreter and other libraries. JDK (Java Development Toolkit) contains JRE, Javac and other tools.

# High performance

>[!info]
>Bytecode can be translated at runtime into machine code for the particular CPU the application is running on.

