---
layout: default
title: Observation Log
description: Things we've noticed while working on the project
permalink: /log
---

# Observation Log

## Algorithms

### One Target Optimal Play

- A single tile target card can be solved fairly easily. The algorithm simply needs to calculate the x-distance
and the y-distance of each valid card from the target location, add one to the count if a flip is necessary, then
choose the tile with the lowest value and move it to the target location so that either the x-distance or y-distance
decrements with each move.
- Complications are introduced with more complicated target cards, because the order in which tiles are moved into
position can matter. Swapping two tiles could move one tile closer and another further away from their respective
target destinations. Conversely, one swap could bring each tile involved closer to their targets, essentially meaning
that two moves are made in one.
- The idea of point sum value, which is the total number of moves necessary to get a given board to a target state,
can represent these isses. In the first case, the point sum value changes by zero; in the second, by two.
- Point sum value can therefore tell us how to make the optimal moves.

### Point Sum Value

- Point sum value is the total number of moves necessary to get a given board state to a given target state.
- There are complications in calculating this. Just calculating it by taking the closest valid tile might not work,
because that tile could be closest to another slot that needs it.
- **NOTE:** Multiple point sum values would have to be calculated and the lowest valid one (where no single tile is reserved by the algorithm twice) chosen.

### Tree Search

- For optimal memory shenanigans, tile grids can be represented in a minimum of 27 bits. There are eight tile types, meaning every type can be represented in
3 bits, as $$2^3 = 8$$. And $$3 \cdot 9 = 27$$, which is where we get our total. The convention we're running with is as follows:

| 000 | 001  | 010  | 011  | 100   | 101  | 110  | 111  |
|-----|------|------|------|-------|------|------|------|
| Sun | Moon | Fish | Bird | Horse | Boat | Seed | Tree |


- As such, the binary string `000 010 100 111 111 101 011 110 100` would represent a grid as follows:

|       | 0    | 1    |  2    |
|-------|------|------|-------|
| **0** | Sun  | Fish | Horse |
| **1** | Tree | Tree | Boat  |
| **2** | Bird | Seed | Horse |

- This requires interpretation after retrieving a tree, but massively reduces the memory demands of storing the results of a tree search. Tree transversal would also be 
much faster.
- Binary strings are also easy to mask. Modifications to the stored trees could also potentially be applied via bit shifting.  

### Parity of Point Sums

Each individidual board has either an even or odd number of "moved" point-sum values but not both. Take for example a board with an optimal point sum value of 3.
In this scenario, all other possible ways to reach the success state all have an odd point sum value. The same case is true for even point sum values. No board
combination will have both odd and even point sum values for a specific target in a specific position on the board.

  
    
