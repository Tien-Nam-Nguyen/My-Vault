---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Functional
published: true
created: 2023-11-16 17:28
modified: 2023-11-16T23:01:00
folder: Tech
---
>[!note]
>Variables in functional languages do not vary


# Immutability and architecture

All concurrent update problems are due to mutable variables. You cannot have those problems when using functional programming.

You should interested in this if you want your system robust in the presence of multiple threads and processors.

# Segregation of mutability

The most common way is to separate the services into immutable components. Those components is purely functional and can communicate with other non-functional components.

It is common practice to use some kind of *transactional memory* to protect mutable variables from concurrent updates.

![Imgur](https://i.imgur.com/3eIUiu3.png)

# Event sourcing 

Event sourcing is a strategy wherein we only store transactions. When the state is required, we apply all the transactions from the beginning of time. Nothing ever gets deleted or updated, our applications are not CRUD, they are just CR. Also because neither deletions nor updates occur, there's no concurrent issues. The application become entirely functional.