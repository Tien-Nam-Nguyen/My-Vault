---
type:
  - Chapter
tags:
  - Architecture
  - Clean
published: true
created: 2024-02-02 17:52
modified: 2024-02-03T21:06:00
folder: Clean Architecture
---
>[!note]
>*The primary purpose of architecture is to support the life cycle of the system. Good architecture makes the system easy to understand, easy to develop, easy to maintain, easy to deploy. The ultimate goal is to minimize the lifetime cost of the system and maximize programmer productivity*.

# Operation

>[!note]
>The impact of architecture on operations seems to be less dramatic than on development, deployment and maintenance.

The architecture should some how reveal the operation to the developers.

# Keeping options open

>[!note]
>There are two major element of a software: policy and details. The policy embodies the business, the true value. The details just are those things that can interact with policy in technical ways.

So you can leave those technical details options for later decisions.


# Conclusion

>[!note]
>Good architects carefully separate details from policy, and then decouple the policy from the details so thoroughly that the policy has no knowledge of the details and does not depend on the details in any way. Good architects design the policy so that decisions about the details can be delayed and deferred for as long as possible.
