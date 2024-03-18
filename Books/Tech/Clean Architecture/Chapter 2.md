---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Software
published: true
created: 2023-10-31 10:08
modified: 2023-11-12T09:35:00
folder: Tech
---
# Value of software system
Every software provides two values to the stakeholders: behavior and structure:

## Behavior

Developers provide this by helping stakeholders make a functional specification, or requirements document.Then we write code to satisfy these.

When the machine violates those requirements, programmer need to debug. Many programmers believe that is entirety of their job. They are sadly mistaken.

## Architecture

Software **must be soft**, it must be easy to change. When stakeholders change their mind about a feature, that change should be simple and easy to make. The difficulty in making this change should be proportional only to the scope of the change. Developers must fit this feature "puzzle piece" into a complexity program. Each new request is harder than the last, because the shape of the system is not match the shape of the request.

The problem is the architecture. The more this architecture prefers one shape over another, the more likely new features will be harder and harder to fit into that structure. Therefore architectures should be as shape agnostic are practical.

# The greater value

Function or architecture? Which is more important for system, workable or easy to change? 

- If a program works but impossible to change, then it won't work when the requirements change. Therefore it will become useless
- If a program does not work but it easy to change, then developers can make it work, and keep it working as requirements change. 

# Eisenhower's matrix

>[!quote] Eisenhower
>*I have two kinds of problem, the urgent and the important. The urgent are not important, and the important are never urgent*
 

The development team has to fight against management team for best architecture that easily modified, easily extended.




