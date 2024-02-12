# Shifting Stones 
### Basic Info
Shifting Stones is a game played on a 3x3 grid of tiles. There are a total of 9 tiles, each belonging to one of four tile types. 
Each tile has two faces, so there are a total of 8 possible faces that any given grid position could contain.
The breakdown of tiles is as follows:
- 1 tile with Sun/Moon faces
- 2 tiles with Fish/Bird faces
- 3 Tiles with Horse/Boat faces
- 3 Tiles with Tree/Seed faces

Given these parameters, the total number of unique configurations possible on the grid can be calculated as follws:

9!/1!(9 - 1)! * 8!/2!(8 - 2)! * 6!/3!(6 - 3)! * 3!/3!(3 - 3)! * 2⁹ = 2,580,480

or

₉C₁ * ₈C₂ * ₆C₃ * ₃C₃ * 2⁹ = 2,580,480

The objective of the game is to match patterns given on cards to the grid. For example, a player might want to arrange the grid so that a horse is directly above a boat. 
On a turn, a player can discard one of their cards to move a tile either horizontally or vertically (but not diagonally), or to flip a tile. This means the total possible number on moves on a given turn is 21.
A player can also skip their turn to draw two more cards, but they cannot do this two turns in a row. Players start with four cards.
### Terminology
The nomenclature for the board is below.
Grid convention:
[a0 a1 a2]
[b0 b1 b2]
[c0 c1 c2]
Tile convention:
Sun: A1
Moon A2
Fish: B1
Bird: B2
Horse: C1
Boat: C2
Seed: D1
Tree: D2

Additionally, we have several concepts that are used in the implementation of the program.
 - Success State: A board position that corresponds to the card, such that the card can be played with no more movements.
 - Point value is a measure of how many moves, and thus how many discards is needed to complete a card. Each flip or movement increases by one point. Exceeding three points means a card is nonviable and should be treated as discard fodder.
 - Point sum is the measure of the total sum of points needed  to achieve a success state given a card and board. 
