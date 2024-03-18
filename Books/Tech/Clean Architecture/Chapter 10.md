---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - SOLID
  - ISP
published: true
created: 2023-11-22 14:56
modified: 2023-11-22T15:31:00
folder: Tech
---
![Imgur](https://i.imgur.com/621JiXE.png)

*User1* use *op1*, *User2* use *op2*,... The source code of *User1* will inadvertently depend on *op2* even it does not call them (because when op2's code changed, the OPS.java become new when *User1* import it)

This problem is solved by segragating the operations into interfaces:

![Imgur](https://i.imgur.com/pveG2p7.png)

# ISP and language

Statically typed languages like Java force us to create declarations use *import*, *include*, .... which create source code dependencies that force recompilation. Dynamically typed languages do not suffer this.

# ISP and architecture

In general, it is harmful to depend on modules that contain more than you need. 

![Imgur](https://i.imgur.com/3ucjaIo.png)

Suppose that D contains features F does not use, so S does not care too. Changes to those features in D may cause redeployment of F, therefore also S. A failure in one of those D's features can cause failure for the whole system S.


