---
type:
  - Chapter
tags:
  - Architecture
  - Clean
published: true
created: 2023-11-28 10:51
modified: 2024-01-27T10:08:00
folder: Tech
---
Components are the smallest entities that can be deployed as part of a system. In Java they are jar files. Well-designed components always have ability to be independently deployable and developable.

# Relocatability

The compiler was changed to output binary code that could be relocated in memory by a smart loader. The loader would be told where to load the relocatable code. It adds the starting address to any memory reference addresses in the binary.

If a program called a library function, the compiler would emit that name as *external reference*. If a program defined a library function, the compiler would emit that name as *external definition*. Then the loader could *link* the external references to the external definitions

# Linkers

The loading and linking were separated into two phases. Programmers took the slow part: linking using linker. The output of linker was a linked relocatable that a relocating loader could load very quickly. This allowed programmers to prepare an executable using the slow linker, but then they could load it quickly at any time.

>[!example]
>Source modules were compiled from *.c* to *.o* files, then fed into the linker to create executable files that could be quickly loaded. 


