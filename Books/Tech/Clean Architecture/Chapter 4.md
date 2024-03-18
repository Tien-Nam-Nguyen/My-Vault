---
type:
  - Chapter
tags:
  - Architecture
  - Clean
  - Software
  - Structured
published: true
created: 2023-11-12 16:57
modified: 2023-11-16T16:00:00
folder: Tech
---
# Proof 

During Dijkstra's investigation, he discovered that certain use of *goto* statements prevent modules from being decomposed recursively into smaller units, thereby preventing use of divide-and-conquer approach for reasonable proofs.

Other uses of *goto* did not have this problem. These uses corresponded to simple statements such as *if/then/else* and *do/while*. Modules that used only those kinds of control structures could be recursively subdivided into probable units.

# Functional decomposition

Structured programming allows modules to be recursively decomposed into provable units. Each high level function can be decomposed into lower-level functions. Each of those can be represented using the restricted control structures of structured programming.

By following these discipline, programmers can break down large systems into modules that could be further broken down into tiny provable functions.

>[!note]
>*There's no formal mathematical proofs for Euclidean hierarchy of theorems*
# Science to the rescue

Mathematical proofs are not the only strategy for proving something correct. Another highly successful strategy is the *scientific* method.

>[!note] Nature of scientific theories and laws
>*They are falsifiable but not provable*


# Tests

>[!quote] Dijkstra
>*Testing shows the presence, not the absence, of bugs*

We show correctness by failing to prove incorrectness.








