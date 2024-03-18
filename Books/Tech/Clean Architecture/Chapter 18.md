---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Boundaries
published: true
created: 2024-02-08 11:49
modified: 2024-02-08T15:15:00
folder: Clean Architecture
---

# The dreaded monolith

Higher level component should be protected (called) through boundaries by lower level component:

Low-level *Client* calls high-level *Service*:

![Imgur](https://i.imgur.com/Ykz1Qzj.png)

High-level *Client* calls low-level *Service*:

![Imgur](https://i.imgur.com/hxVUwzj.png)

