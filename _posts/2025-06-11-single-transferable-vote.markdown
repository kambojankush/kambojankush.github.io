---
layout: post
title: "STV - Single Transferable Vote"
date: 2025-06-11 18:20:00 +0530
categories: random
---

[Single Transferable Vote (STV)](https://en.wikipedia.org/wiki/Single_transferable_vote) is a voting system where voters rank candidates in order of preference. 
It’s designed to achieve proportional representation while minimizing wasted votes.

<h3>The Core Concept:</h3>

1. **Ranking Candidates:**
Each voter lists candidates in order of preference — 1st, 2nd, 3rd, and so on.

2. **Setting the Quota:**
A quota (minimum number of votes needed to get elected) is calculated based on:
    * Total number of valid votes cast.
    * Number of available seats.

3. **Counting the Votes:**
    * In the first round, only first preference votes are counted.
    * Any candidate who meets or exceeds the quota is immediately elected.

4. **Transferring Surplus Votes:**
    * If a candidate has more votes than needed, the surplus is transferred to the next preferred candidates on those ballots.
    * This simulates what would happen if the elected candidate was removed from the race.

5. **Eliminating the Lowest:**
    * If no one meets the quota in a round, the candidate with the fewest votes is eliminated.
    * Their votes are transferred to the next preferred candidates on each ballot.

6. **Repeat Until All Seats Are Filled:**
The process of transferring surplus votes and eliminating the lowest continues until all seats are filled.

STV is used in several countries for local or national elections, including Scotland, New Zealand, and Australia, as well as in online platforms like Stack Overflow for electing moderators.


{% raw %}
<iframe width="780" height="450" src="https://www.youtube.com/embed/l8XOZJkozfI?si=1tK33iT5ftwHGX2L" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<br>
{% endraw %}

<br>
Now, there are multiple variations / implementation details for this voting system.
These variations are influenced by multiple factors, including:
* **Vote Counting Methods**: Manual or automated systems may affect how votes are counted and transferred. (_Some people may prefer simplicity over added fairnes_)
* **Quota Calculation**: Some systems use a fixed quota, while others recalculate it in each round, possibly excluding discarded votes.
* **Handling Surplus Transfers**:
    - Some methods transfer just the last bundle of surplus votes.
    - Others redistribute all votes proportionally, factoring in how much of the surplus to move.
* Rules vary on how to resolve ties — by drawing lots, looking at earlier rounds, etc.
* Some systems allow voters to give equal preference to multiple candidates.
* Voters may choose to rank only some candidates, leaving others blank.
