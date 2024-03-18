---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Independence
published: true
created: 2024-02-05 16:48
modified: 2024-02-05T23:00:00
folder: Clean Architecture
---
A good architecture must support the following factors:
# Use cases

>[!note]
A good architecture must expose the use cases such that its intent can be clearly visible at the architectural level.

# Operation

>[!note]
>The architecture must have the ability to handle necessary operation for businesses. This should be left as an open option for future system upgrade/transition.

# Development

Architecture must support development process of teams as Conway's law:

>[!quote]
>*Any organization that designs a system will produce a design whose structure is a copy the organization's communitcation structure*

# Deployment

>[!note]
>A good architecture makes deployment easy and quick. 

# Decoupling layers 

>[!note]
>Although we do not know all the use cases, but the architect can still know basic intent of each component, how different they are to separate and change them for different reasons. 

# Decoupling use cases

>[!note]
>Use cases are vertical slices that cut through those horizontal layers by using many services across layers at the same time. You can separate a layer into smaller vertical slice that more fit to your requirements.

# Duplication

>[!note]
>There are two kinds of duplication: true duplication, in which every change to one instance necessitates the same change to every duplicate and accidental duplication, which codes change for different reasons.

When you are separating use cases, you will be tempted to couple component codes. If you did, it would be a challenge to separate them again in the future.

# Decoupling modes (again)

>[!info]
>There are three levels:
>- **Source level**: dependencies between module sources. All components are executed in the same address space.
>- **Deployment level**: dependencies between deployable units (JAR, DLLs). They can communicate in the same or different processes.
>- **Service level**: dependencies of level of data structure, communicate through network packets (e.g. micro services)

A good architecture will allow a system to be born as a monolith, deployed in a single file, but then to grow into a set of independently deployable units,
and then all the way to independent services and/or micro-services. Later, as things change, it should allow for reversing that progression and sliding all the way back down into a monolith.