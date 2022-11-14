---
layout: post
title: "Intermediate SQL"
date: 2022-11-07 04:20:00 +0530
categories: sql
---

Consolidated page for different sql concepts.

## 1. Joins

Combines columns from one or more tables and produces a new table.
Used to express queries that invlolve data that spans multiple tables.

### 1.1 Different Types of Joins:

![join_types](/assets/images/sql-joins.PNG)
a.) **Inner Join**: Returns rows which have matching values in both left and right relation.
 
b.) **Left Join**: Returns all values from the left relation and matched values from the right relation (appends NULL if there is no match). a.k.a _Left Outer Join_
 
c.) **Right Join**: Returns all values from the right relation and the matched values from the left relation (appends NULL if there is no match). a.k.a _Right Outer Join_
 
d.) **Full Join**: Returns all values from both relations (appends NULL value on the side that does not have a match). a.k.a _Full Outer Join_
 
e.) **Cross Join**: Returns the cartesian product of two relations. (Every possible combination of elements of first relation with elements of second relation).
 
f.) **Semi Join**: Returns values from the left side of the relation that has a match with the right. a.k.a _Left Semi Join_. 
 
**Note**: If one element of left relation matches with 2 elements of right, in that case, a left or inner join will return two rows corresponding to the matching element (1 for each element of right); but the semi join will only return one row.
 
g.) **Anti Join**: Returns values from the left relation that has no match with the right relation. a.k.a _Left Anti Join_. Inverse of _semi join_.


## 2. Nested Queries
TODO:

## 3. Window Functions

From postgres documentation:
> **A window function performs a calculation across a set of table rows that are somehow related to the current row.** This is comparable to the type of calculation that can be done with an aggregate function. However, window functions do not cause rows to become grouped into a single output row like non-window aggregate calls would. Instead, the rows retain their separate identities. **Behind the scenes, the window function is able to access more than just the current row of the query result.**

Window functions compute their result based on a sliding window frame, a set of rows that are somehow related to the current row.

![window_function](/assets/images/window_function_1.PNG)

![window_function2](/assets/images/window_function_2.PNG)

A window frame is a set of rows that are somehow related to the current row. The window frame is evaluated separately within each partition.

![window_function3](/assets/images/window_function_3.PNG)

Default Window Frame:
* If `ORDER BY` is specified, then the frame is `RANGE BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW`.
* Without `ORDER BY`, the frame specification is `ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING`.

```sql
ROWS | RANGE | GROUPS BETWEEN lower_bound AND upper_bound
```

The ROWS, RANGE and GROUPS clauses limit the number of rows considered by the window function within a partition.
* ROWS specifies a fixed number of rows that precede or follow the curret row.
* RANGE / GROUPS logically limit the rows, i.e, they consider the rows based on their vlaue compared to the current row.

Ref: 

- [Window Functions Cheatsheet](https://learnsql.com/blog/sql-window-functions-cheat-sheet/)
- [Julia Kho post](https://towardsdatascience.com/a-guide-to-advanced-sql-window-functions-f63f2642cbf9)
- [Window Frames](https://learnsql.com/blog/difference-between-rows-range-window-functions/)
