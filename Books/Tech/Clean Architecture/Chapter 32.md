---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Framework
  - Commitment
published: true
created: 2024-02-13 18:01
modified: 2024-02-13T20:27:00
folder: Clean Architecture
---
# Asymmetric marriage

 The relationship between between you and the framework author is extraordinarily asymmetric. You must make a huge commitment to the framework, but the author makes no commitment to you.

You couple your code to the framework's classes as tightly as possible as the author's advice in their documentations so that it will work as they expect.
**You take all the risk when you make that commitment**

# The risks

- It tends to violate Dependency rule when you couple their code into your business codes.
- When your application grows, it may outgrow the facilities of the framework
- Your old features can disappeared when new version came out.
- It's hard to switch to another version

# Solution

>[!note]
>Treat the framework as a detail that belongs in outer circles of the architecture.

Don't use framework in your core code. Keep those code in components as plug-in.


