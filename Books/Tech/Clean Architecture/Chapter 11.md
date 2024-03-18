---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - SOLID
  - DIP
published: true
created: 2023-11-22 15:32
modified: 2023-11-28T10:43:00
folder: Tech
---
The most flexible systems are those in which source code dependencies refer (import, include) only to abstractions (interface, abstract class), not to concretions.

We avoid it in our developing systems, not in their libraries.

Stable software architectures avoid depending on volatile concretions, following these practices:

- **Don't refer to volatile concrete class**
- **Don't derive from volatile concrete class**
- **Don't override concrete functions**: concrete functions require source code dependencies. When you override it, you inherit them, not eliminate.
- **Never mention the name of anything concrete and volatile**






