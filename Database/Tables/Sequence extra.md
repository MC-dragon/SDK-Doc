---
uid: Sequencetable
title: Sequence table
---

Use of the Sequence table
=========================

The sequence table contains the next unallocated id for each SuperOffice table. 
Each sequential row has its own id number, which is 10 + the table number in the table listing.

 

When inserting a new row in a table you will need to allocate the id-value to use for this record.

 
Reading and updating the next id-value should always be performed as a single transaction because if someone else reads and updates this information simultaneously, a database error will occur when inserting the new row.

 

Example:

Allocate an id for Contact table

   ([Contact](../Tables/CONTACT.md) is table 5, + 10 = 15)

```SQL
    BEGIN TRANSACTION
    UPDATE Sequence SET next_id = next_id + 1 WHERE id = 15;
    SELECT next_id - 1 FROM Sequence WHERE id = 15;
    COMMIT TRANSACTION
```