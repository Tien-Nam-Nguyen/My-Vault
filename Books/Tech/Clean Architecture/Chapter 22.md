---
type:
  - Chapter
tags:
  - Architecture
  - Clean
published: true
created: 2024-02-08 15:54
modified: 2024-02-08T17:34:00
folder: Clean Architecture
---
![Imgur](https://i.imgur.com/BdWvTxj.png)


# The dependency rule

The further in you go in above circle, the higher level the software becomes.

>[!note]
>*Source code dependencies must point only inward, toward higher-level policies*

# Entities

Entities encapsulate the most general and high-level critical business rules.

# Use cases

It contains application-specific business rules. It implements and orchestrate the flow of data to and from entities, direct those entities to use business rules to achieve the goals of use case.

# Interface adapters

This layer contains a set of adapters that convert data from the format used in use cases and entities to the more convenient format for external agency.

For example, it can contain MVC of a GUI. The model is just data structures that are passed from the controllers to use cases, and are passed backward.

# Frameworks and drivers

This layer is composed of frameworks, databases and tools.

# A typical scenario

![Imgur](https://i.imgur.com/kS3tUdR.png)

>[!info]
>*Controller* packages data using *InputData* and passes it to *UseCaseInteractor* through *InputBoundary*. The *UseCaseInteractor* interprets that data and uses it to control the dance of *Entities*. It also use *DataAccessInterface* to get data from database. Upon completion, *UseCaseInteractor* gathers data from *Entities* and construct *OutputData*. *OutputData* is passed through *OutputBoundary* to *Presenter*. *Presenter* repackages *OutputData* into viewable form - *ViewModel* contains mostly *String*.

