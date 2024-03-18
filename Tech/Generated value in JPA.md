---
type: 
tags:
  - JPA
  - Java
  - SpringBoot
published: true
created: 2023-11-30 21:59
modified: 2023-11-30T22:08:00
folder: Tech
---
# GenerationType.IDENTITY

Generate primary key value by the database itself using the auto-increment column option (database's native support)

# GenerationType.AUTO

The default strategy to generate key value which automatically selects an appropriate strategy based on the database usage.

# GenerationType.TABLE

This strategy use a separate database table to generate primary key. 

# GenerationType.SEQUENCE

This generation-type strategy uses a database sequence to generate primary key values. It requires the usage of database sequence objects, which varies depending on the database which is being used

