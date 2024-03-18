---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - SOLID
  - OCP
published: true
created: 2023-11-17 16:46
modified: 2023-11-21T23:09:00
folder: Tech
---
The Open-Closed Principle (OCP) says:

>[!info]
>A software artifact should be open for extension but closed for modification

In other words, the behavior of a software artifact ought to be extendible, without having to modify that artifact.
# A thought experiment

If component A should be protected from changes in component B, then component B should depend on component A. Why should the *Interactor* hold such a privileged position? Because it contains the business rules.

![Imgur](https://i.imgur.com/fHPGvze.png)


This is how OCP works at the architectural levels. Architects separate functionality based on how, why, and when it changes, and then organize that separated functionality into a hierarchy of components. Higher-level components in that hierarchy are protected from the changes made to lower-level components

Even though our first priority is to protect the *Interactor* from changes to the *Controller*, we also want to protect *Controller* from changes to the *Interactor* by hiding the internals of the *Interactor*

