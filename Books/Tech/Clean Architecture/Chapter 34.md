---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Package
published: true
created: 2024-02-13 23:56
modified: 2024-02-14T00:07:00
folder: Clean Architecture
---
There's many ways to design and code organization:
# Package by layer

Layers should depend only on the next adjacent lower layer. Each layer is implemented as a package.

![Imgur](https://i.imgur.com/M3nwzg6.png)

# Package by feature

All of the types are placed into a single package. The top-level organization of the code now screams clearly something about the business domain.

![Imgur](https://i.imgur.com/HXPkR10.png)

# Ports and adapters

As uncle Bob said, your business code should be independent and separated from implementation details. It is composed of an "inside" and an "outside"

![Imgur](https://i.imgur.com/HiDrwtr.png)

The outsides should depend on the inside, never the other way around.

![Imgur](https://i.imgur.com/51RIYKa.png)

# Package by component

![Imgur](https://i.imgur.com/QZWwulF.png)
