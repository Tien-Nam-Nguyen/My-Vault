---
type:
  - Chapter
tags:
  - Architecture
  - Clean
published: true
created: 2024-01-27 10:10
modified: 2024-01-27T23:30:00
folder: Clean Architecture
---
# The reuse/release equivalence principle

>[!info]
>Classes and modules that are grouped together into a component should be *releasable* together

# The common closure principle

>[!quote]
>*Gather into components those classes that change for the same reasons and at the same times. Separate into different components those classes that change at different times and for different reasons*

If two classes are so tightly bound that they always change together, then they belong in the same component. This minimizes the workload related to releasing, revalidating and redeploying the software.

# The common reuse principle

>[!quote]
>*Don't force users of a component to depend on things they don't need*

When one component uses another, a dependency is created between the components.

When we depend on a component, we want to make sure we depend on every class in that component. We want to make sure that the classes that we put into a component are inseparable - that it is impossible to depend on some and not on the others.

# The tension diagram for component cohesion

![Imgur](https://i.imgur.com/C2ihPml.png)

Generally, projects tend to start on the right hand side of the triangle, where the only sacrifice is reuse. As the project matures, and other projects begin to draw from it, the project will slide over to the left. This means that the component structure of a project can vary with time and maturity

