---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - SOLID
  - SRP
published: true
created: 2023-11-16 23:01
modified: 2023-11-16T16:45:00
folder: Tech
---
There will be more than one "user" or "stakeholder" wants the system to change in the same way.  We use the word "actor" instead as a group of user/stakeholder.

>[!info]
>A module should be responsible to one, and only one, actor.

The word "module" here means a source file component. 

The best way to understand is by looking at symptoms of violating it.

# Symptom 1: Accidental duplication

![Imgur](https://i.imgur.com/Vsz47KC.png)

Three methods are responsible to three very different actors:
- CalculatePay() is specified by accounting department, which reports to the CFO
- reportHours() is specified by human resources department, which report to the COO
- save() is specified by database administrators, who reports to CTO

By putting the source code for these three methods into a single class, the developers have coupled each of these actors to the others. This coupling can cause affect to each other team. When one requirements of a team is fulfil, other teams can be negatively affect without knowing.

>[!note]
>SRP says to separate the code that different actors depend on

# Symptom 2: Merges

Two different teams make some changes in the same places, and their changes collide. The result is a merge. The way to avoid this is to *separate code that support different actors*

# Solutions

![Imgur](https://i.imgur.com/AgW8Znx.png)

The most obvious way is to separate data from functions. Each class holds only the source code for it particular function. They do not know about each other. The [[Books/Tech/Clean Architecture/Chapter 7#Symptom 1 Accidental duplication|accidental duplication]] is avoided.

The downside of this solution is that there are many classes to track. This can be solved using *Facade*.

![Imgur](https://i.imgur.com/IDa315x.png)






