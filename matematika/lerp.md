## Linear Interpolation (LERP)

In games, we oft en need to find a vector that is midway between two known vectors. For example, if we want to smoothly animate an object from point A to point B.

A linear interpolation is a simple mathematical operation that finds an intermediate point between two known points. The operation is defined as follows, where β ranges from 0 to 1 inclusive:
```
L = LERP (A, B, β) = (1 − β) A + β B
= [(1 − β) A x + β B x, (1 − β) A y + β B y, (1 − β) A z + β B z].
```

Geometrically, `L = LERP(A, B, β)` is the position vector of a point that lies β percent of the way along the line segment from point A to point B. Mathematically, the LERP function is just a weighted average of the two input vectors, with weights (1 – β) and β, respectively. Notice that the weights always add to 1.
