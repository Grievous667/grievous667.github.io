### Algorithms
One Target Optimal Play:
- A single tile target card can be solved fairly easily. The algorithm simply needs to calculate the x-distance and the y-distance of each valid card from the target location, add one to the count if a flip is necessary, 
then choose the tile with the lowest value and move it to the target location so that either the x-distance or y-distance decrements with each move.
- Complications are introduced with more complicated target cards, because the order in which tiles are moved into position can matter. Swapping two tiles could move one tile closer and another further away from their respective target destinations.
Conversely, one swap could bring each tile involved closer to their targets, essentially meaning that two moves are made in one.
- The idea of point sum value, which is the total number of moves necessary to get a given board to a target state, can represent these isses. In the first case, the point sum value changes by zero; in the second, by two.
- Point sum value can therefore tell us how to make the optimal moves.

### Point Sum Value
- Point sum value is the total number of moves necessary to get a given board state to a given target state.
- There are complications in calculating this. Just calculating it by taking the closest valid tile might not work, because that tile could be closest to another slot that needs it. 
Multiple point sum values would have to be calculated and the lowest valid one (where no single tile is reserved by the algorithm twice) chosen.
