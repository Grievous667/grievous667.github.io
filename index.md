Game Information: https://grievous667.github.io/game_info
# MRS: Shifting Stones Running Documentation 
## Overarching Objectives:
- Determine and implement an algorithm that finds an optimal set of moves to get the board to a given state.
- Determine and implement an algorithm that performs one turn optimal play.
- Determine the longest a game can run with optimal play (?).


## Jan 24, 2024
### Accomplished:
- Basic Shifting Stones computer program created.
- Tile breakdown:
  - 3 Boat/Horse Tiles
  - 3 Seed/Tree Tiles
  - 2 Fish/Bird Tiles
  - 1 Sun/Moon Tile

### Objectives:
- Finish code/implement correct tile generation. 
- Play game/search for patterns.
- Create tile/grid naming system.
  
## Jan 29, 2024
### Accomplished:
- Shifting Stones program tile generation corrected.
- Tile nomenclature recorded.
  - Grid convention:
    - [a0 a1 a2]
    - [b0 b1 b2]
    - [c0 c1 c2]
  - Tile convention:
    - Sun: A1
    - Moon A2
    - Fish: B1
    - Bird: B2
    - Horse: C1
    - Boat: C2
    - Seed: D1
    - Tree: D2
- Code organized.
- Code modularized.
- Total possible grid configurations calculated:
  - ₉C₁ * ₈C₂ * ₆C₃ * ₃C₃ * 2⁹ = 2,580,480
- Total moves on a given turn calculated:
  - 21

### Objectives:
- Implement card input method.
- Update running document.
- Depth-first search algorithm.
- Determine algorithm patterns by hand.
- Monte Carlo Search Tree: https://www.cs.swarthmore.edu/~mitchell/classes/cs63/f20/reading/mcts.html
