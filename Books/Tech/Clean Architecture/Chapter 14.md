---
type:
  - Chapter
tags:
  - Architecture
  - Clean
published: true
created: 2024-01-28 20:43
modified: 2024-02-02T17:51:00
folder: Clean Architecture
---
The next three principles deal with the relationships between components.

# The acyclic dependencies

>[!quote]
>*Allow no cycles in the component dependency graph*

"The morning after syndrome" can be solved using two solutions which came from the telecommunications industry: "the weekly build" and Acyclic dependencies principle.

# The weekly build

>[!info]
>It works like this: all developers ignore each other for the first four days of the week, they all work on private copies. Then on Friday, they integrate all their changes and build the system.

## Eliminating dependency cycles

The solution for this is to partition the development into releasable components. When developers get a component working, they release it for use the other developers.

There is no single point in time when all developers must come together and integrate everything they are doing.

To make this work successfully, you must manage the dependency structure of the components such that there can be no cycles (DAG)

![Imgur](https://i.imgur.com/j8I9Kku.png)

You can find out which components are affected by a release by following the arrow backwards. If you want to test your component (*Presenter*), you just need to build it with the components depend on it (*View*, *Main*).

# The effect of a cycle in the component dependency graph

![Imgur](https://i.imgur.com/iiywxpE.png)

The first trouble: *Database* must be compatible with *Authorizer* because *Entities* depends on *Authorizer*. It also must be compatible with *Interactors* for the same reason. This makes *Database* hard to release and test.

# Breaking the cycle

>[!info]
> It is always possible to break a cycle and reinstate the dependency graph as DAG. There are two primary mechanism:
> - Apply [[Chapter 11 | DIP]]. 
> 
>![Imgur](https://i.imgur.com/kqq6tGl.png) 
> - Create a new component that both component depend on. Move the class they both depend on into that new component.
> 
> ![Imgur](https://i.imgur.com/UxdQ7WH.png)
> 


# Top-down design

The component structure cannot be designed from the top down. It is not one of the first things about the system that is designed, but rather evolves as the system grows and changes

if we tried to design the component dependency structure before we designed any classes, we would likely fail rather badly. We would be unaware of any reusable elements, and we would almost certainly create components that produced dependency cycles.

Thus the component dependency structure grows and evolves with the logical design of the system.

# The stable dependencies principle

>[!quote]
>*Depend in the direction of stability*

Some volatility is necessary if the design is to be maintained. Any volatile component should not be depended on by a component that is difficult to change.

# Stability

>[!info]
>It's the ability of a software that is hard to change.

![Imgur](https://i.imgur.com/9puH1CV.png)

Three component depend on *X*, so it has three good reasons not to change. *X*  depends on nothing, so it is independent.

![Imgur](https://i.imgur.com/T5z0guo.png)

*Y* is very unstable and dependent.
# Stability metrics

One way is to count the number of dependencies relate to that component:
- *Fan-in*: incoming dependencies
- *Fan-out*: outgoing dependencies
- I: instability = *Fan-out* / (*Fan-in* + *Fan-out*)

>[!example]
>![Imgur](https://i.imgur.com/IGdWWI2.png)
>Component C (Cc)
>- *Fan-in* = 3
>- *Fan-out* = 1
>- *I* = 1 / 4

The *I* metric can easily be computed when you organized code one class each file. In Java, this metric can be computed by counting *import* statements and qualified names

# The stable abstractions principle

On one hand, it says that a stable component should be abstract so that its stability does not prevent it from being extended. On the other hand, it says that unstable component should be concrete. Thus, stable component should be interface

# Measuring abstraction

>[!info]
>The *A* is a measure of abstractness of a component. It is the ratio of interface to the total number of classes.

![Imgur](https://i.imgur.com/PlYNL77.png)

You should not have your component in those two dangerous zones.

# Distance from the main sequence

You would want your component to be as far as possible from the *Main Sequence* line using distance metric *D* = |*A* + *I* - 1|

Any component that has D value not close to zero must be reexamined and restructured.

You can conduct a statistical analysis for your design to identify bad outliers.

![Imgur](https://i.imgur.com/XxVVunk.png)

