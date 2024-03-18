---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Software
published: true
created: 2023-10-29 22:16
modified: 2023-10-31T10:08:00
folder: Tech
---
# What is design and architecture

There is no different between design and architecture. The word "architecture" is often used to describe high level structure, whereas "design" seems to imply structure at low level. In software, both low level and high level define the shape of the system.


> [!quote]
> *The goal of software architecture is to minimize the human resources required to build and maintain the required system*.

## Signature of a mess

When systems are thrown together in a hurry, when the number of programmers is increasing and when little thought is given to the cleanliness of the code or structure of the design, you will come to an ugly end.

![Imgur|500](https://i.imgur.com/PqUbysH.png)

The figure above is from the developer's view. They started at 100% productivity, but with each release the productivity declined and approach asymptotically to zero.

![Imgur|500](https://i.imgur.com/RwXzJpH.png)

This figure is from the executive's view. In some first releases, few hundred thousand dollars bought a lot of productivity, but the final with huge dollars bought nothing. Immediate action is necessary to stave off disaster.

## What went wrong?

Developers often buy into familiar lie: "We can clean it later, just go to the market first". But in reality, they never clean it. They cannot go back to clean because they've got to to get the next feature done, and the next, and the next. And so the mess builds, and productivity heavily declined.

This is a prove that developers are too confident in their ability to remain productive. The fact is that *making messes is always slower than staying clean*, no matter what.

![Imgur|500](https://i.imgur.com/8wMk1WD.png)


>[!quote]
>*The only way to go fast, to to go well*

>[!Quote]
> *Their overconfidence will drive the redesign into the same mess as the original project*
