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

> a.) **Inner Join**: Returns rows which have matching values in both left and right relation.
> 
> b.) **Left Join**: Returns all values from the left relation and matched values from the right relation (appends NULL if there is no match). a.k.a _Left Outer Join_
> 
> c.) **Right Join**: Returns all values from the right relation and the matched values from the left relation (appends NULL if there is no match). a.k.a _Right Outer Join_
> 
> d.) **Full Join**: Returns all values from both relations (appends NULL value on the side that does not have a match). a.k.a _Full Outer Join_
> 
> e.) **Cross Join**: Returns the cartesian product of two relations. (Every possible combination of elements of first relation with elements of second relation).
> 
> f.) **Semi Join**: Returns values from the left side of the relation that has a match with the right. a.k.a _Left Semi Join_. 
> 
> **Note**: If one element of left relation matches with 2 elements of right, in that case, a left or inner join will return two rows corresponding to the matching element (1 for each element of right); but the semi join will only return one row.
> 
> g.) **Anti Join**: Returns values from the left relation that has no match with the right relation. a.k.a _Left Anti Join_. Inverse of _semi join_.

![join_types](/assets/images/sql-joins.PNG)

## 2. Nested Queries
TODO:

## 3. Window Functions
TODO:
