---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Boundaries
published: true
created: 2024-02-05 23:14
modified: 2024-02-08T11:48:00
folder: Clean Architecture
---
>[!note]
>A good architecture allows decision like decision about frameworks, databases, web servers, ... to be made at the latest possible moment without significant impact.


# Boundary example

![Imgur](https://i.imgur.com/WEvHSXH.png)

None of these classes know *DatabaseAccess* exists.

![Imgur](https://i.imgur.com/ppecuZt.png)

The direction is important. It shows that *Database* does not matter to *BusinessRules*, but *Database* cannot exist without *BusinessRules*.

# Plugin architecture

![Imgur](https://i.imgur.com/2xBYod7.png)

*BusinessRules* should be protected and independent from optional third party modules.

