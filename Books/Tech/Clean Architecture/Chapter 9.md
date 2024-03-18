---
type:
  - Chapter
tags:
  - Clean
  - Architecture
  - SOLID
  - LSP
published: true
created: 2023-11-21 23:09
modified: 2023-11-22T14:56:00
folder: Tech
---
>[!quote] Barbara Liskov
>*What is wanted here is something like the following substitution property: If for each object o1 of type S there is an object o2 of type T such that for all programs P defined in terms of T, the behavior of P is unchanged when o1 is substituted for o2 then S is a subtype of T.*


# Guiding the use of inheritance

![Imgur](https://i.imgur.com/h31ZYyJ.png)

This design conforms LSP because *Billing* does not depend on two subtypes.

# The square/rectangle problem

![Imgur](https://i.imgur.com/ePXuxdD.png)

Since *User* believe it is communicating with a *Rectangle*, it could easily get confused (when calculate area). *Square* is **not** a proper subtype of *Rectangle*.



