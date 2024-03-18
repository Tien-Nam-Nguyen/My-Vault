---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Service
published: true
created: 2024-02-08 21:36
modified: 2024-02-09T21:48:00
folder: Clean Architecture
---
# Service benefits?
## The decoupling fallacy

>[!note]
>Services are not totally decoupled. They can still be coupled by shared resources within processor or network, especially by the shared data

## The fallacy of independent development and deployment

>[!note]
>To the extent that they are coupled by data or behavior, the development, deployment and operation must be coordinated
>

In case of adding new features to this system, functional decomposition services are very vulnerable to this feature that cut across all behaviors. All component will have to change.

Original system with just taxi feature:

![Imgur](https://i.imgur.com/x4NOmaP.png)


System with additional kittens shipping feature: solved using abstract base classes with component-based architecture.

![Imgur](https://i.imgur.com/PjP32Gy.png)

Can we do that for services? **YES**!

>[!note]
>You can think of a service in Java as a set of abstract classes in one or more jar files, new feature as another jar file that extend those abstract classes.

![Imgur](https://i.imgur.com/y6wZD6G.png)



