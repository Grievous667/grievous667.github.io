---
layout: default
title: Proofs and Explainations
description: "\"How does that work?\""
permalink: /proofs/board-configs
---

# Finding the total possible number of board configurations

## Modeling the situation using the game

Note that within the game, the Sun/Moon tile appears once, the Fish/Bird tile appears twice, and
the Seed/Tree and Horse/Boat tiles appear three times. This means that on a $$ 3 \times 3 $$ board,
we can assign the Sun/Moon tile in 9 ways. Once this tile is assigned a spot, we can then assign the
two Fish/Bird tiles any of 8 ways. It follows that we can assign a spot to the Seed/Tree tiles any of
6 ways, and finally the Horse/Boat tiles can be assigned any of 3 ways. Using this information, we can
Calculate the total number of grid con figurations given the 9 tiles. Modeling this situation using
combinatorics, we find that:

$$
  \begin{array}{l}
  \rm{Configurations} &= \displaystyle {9 \choose 1} \cdot {8 \choose 2} \cdot {6 \choose 3} \cdot {3 \choose 3} \\
  &= \displaystyle \frac{9!}{1! \ 8!} \cdot \frac{8!}{2! \ 6!} \cdot \frac{6!}{3! \ 3!} \cdot \frac{3!}{3! \ 0!} \\
  \end{array}
$$

However, this result doesn't take into account that every tile can be flipped. To determine this result,
we must first find how many ways we can flip tiles. Each tile has two "states" (flipped or not flipped),
and because each of the 9 tiles could have either of these two states, we can assign board states in a
total of $$ 2^9 $$ ways. Multiplying this value by the total number of configurations found above yields
the total number of board configurations:

$$ \rm{Total \ Configurations} = \displaystyle \frac{9!}{1! \ 8!} \cdot \frac{8!}{2! \ 6!} \cdot \frac{6!}{3! \ 3!} \cdot \frac{3!}{3! \ 0!} \cdot 2^9 $$

Evaluating we find that:

$$
  \begin{array}{l}
  &= \displaystyle \frac{9!}{1! \ 8!} \cdot \frac{8!}{2! \ 6!} \cdot \frac{6!}{3! \ 3!} \cdot \frac{3!}{3! \ 0!}\cdot 2^9 \\
  &= 9 \cdot 28 \cdot 20 \cdot 1 \cdot 512 \\
  &\boxed{= 2,580,480 \rm{\ total \ board \ configurations}}
  \end{array}
$$

## Modeling the situation generically

This solution can be generalized to show that it works not only for a $$ 3 \times 3 $$ game board, but for any
$$ n \times n $$ board.

Let $$ n $$ be the number of tiles in one row or column of the board, such that the board is of size
$$ n \times n $$. Let $$ k $$ be the number of groups of tiles we have to assign a space to. In the
original Shifting Stones game, $$ k = 4 $$ because we have four groups, or types, of tiles that can be
used. Let $$ g_1, g_2, ..., g_k $$ be the number of tiles in each of these $$ k $$ groups such that
$$ g_1 + g_2 + \dots + g_{k - 1} + g_k = n $$. In the original game, we have:

$$
    \begin{array}{l}
    g_1 = 1 \\
    g_2 = 2 \\
    g_3 = 3 \\
    g_4 = 3
    \end{array}
$$

And $$ 1 + 2 + 3 + 3 = 9 $$.

Using the same equations as before, we can express the total number of board combinations generically.
For the first tile group, we can choose $$ g_1 $$ board spots $$ n $$ ways. For the second tile group, we
can choose $$ g_2 $$ board spots $$ n - g_1 $$ ways. This pattern follows up to the $$ n^{\text{th}} $$ group,
where we choose $$ g_n $$ board spots $$ n - g_1 - g_2 - \dots - g_{n - 1} $$ ways. To account for flips,
we multiply the number of combinations before flips by $$ 2^n $$:

$$
  \begin{array}{l}
  \rm{Total \ Configurations} &= \displaystyle {n \choose g_1} \cdot {n - g_1 \choose g_2 } \cdot \dots \cdot {n - g_1 - g_2 - \dots - g_{n - 2} \choose g_{n - 1}} \cdot {n - g_1 - g_2 - \dots - g_{n - 2} - g_{n - 1} \choose g_n} \cdot 2^n \\
  &= \displaystyle \frac{n!}{g_1! \left(n - g_1\right)!} \frac{\left(n - g_1\right)!}{g_2! \left(n - g_1 - g_2\right)!} \cdot \dots \cdot \frac{\left(n - g_1 - g_2 - \dots - g_{n - 2}\right)!}{g_{n - 1}! \left(n - g_1 - g_2 - \dots - g_{n - 2} - g_{n - 1}\right)!} \cdot \frac{\left(n - g_1 - g_2 - \dots - g_{n - 2} - g_{n - 1}\right)!}{g_n! \left(n - g_1 - g_2 - \dots - g_{n - 1} - g_n\right)!} \cdot 2^n
  \end{array}
$$

Note that we can simplify this equation, as factorials in the numerator can cancel with factorials in the
denominator:

$$ = \displaystyle \frac{2^n \cdot n!}{g_1! g_2! \dots g_{n - 1}! g_n! \left(n - g_1 - g_2 - \dots - g_{n - 2} - g_n\right)!} $$

Recall that $$ g_1 + g_2 + \dots + g_{k - 1} + g_k = n $$. Observe that: \\
$$
  \begin{array}{l}
  g_1 + g_2 + \dots + g_{k - 1} + g_k &= n \\
  n - (g_1 + g_2 + \dots + g_{k - 1} + g_k) &= 0 \\
  n - g_1 - g_2 - \dots - g_{k - 1} - g_k &= 0
  \end{array}
$$

Thus, $$ \left(n - g_1 - g_2 - \dots - g_{n - 1} - g_n\right)! = 0! = 1 $$, so we can simplify our equation to:

$$ \displaystyle \boxed{= \frac{2^n \cdot n!}{g_1! g_2! \dots g_{n - 1}! g_n!}} $$
