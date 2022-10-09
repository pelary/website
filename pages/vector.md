---
title: Vectors
---

Vectors.

## Scalar

Sounds like "scale". A scalar quantity. A numeric value. Something that has a _magnitude_.

A Vector is something that has a magnitude as well as a direction.

## Vectors in 2D

[1.1 What is a Vector? - The Nature of Code - YouTube](https://www.youtube.com/watch?v=bKEaK7WNLzM)

Vectors are represented as an arrow. A set of (x,y) coordinates can be a vector that provides instructions for getting from (0,0) to (x,y).

If we draw an arrow from (0,0) to (x,y), that line's length is the magnitude, and the direction it's pointing is the direction, which can be represented as an angle (theta, Θ) relative to its origin point (relative to horizontal plane?)

The vector is just the arrow. The coordinates are not the vector. The vector doesn't have a position. It just represents instructions from getting to one position to another.

## Vectors in p5

A Vector object in [[p5]] stores the "components" of the vector — the (x,y) coordinates. Or three coordinates in 3D.

`createVector([x],[y],[z])`

(`[x]` the square brackets mean it's optional)

### Vector Addition and Subtraction

Vector addition is the same as scalar addition.

`(1,1) + (1,1) = (2,2)` (That's probably not a correct notation)

Same for subtraction.

It's useful to look at this happening on a diagram: [‪Vector Addition‬](https://phet.colorado.edu/sims/html/vector-addition/latest/vector-addition_en.html)

In p5:

- [reference \| add()](https://p5js.org/reference/#/p5.Vector/add)
- [reference \| sub()](https://p5js.org/reference/#/p5.Vector/sub)

### Vector multiplication

p5 offers `mult()` for _scaling_ vectors. Multiplying by a scalar quantity.

The direction stays the same, only the magnitude changes.

### Random Vectors

In p5, `random2d()` creates a random two dimensional vector.

## Normalizing vectors

Make a vector into a unit vector. A unit vector has a magnitude of 1.

`mag()` returns the magnitude of a vector. A scalar length. It derives the value by using pythagoras. Effectively it takes the x and y values as two sides of a triangle and uses `c = sqrt(a^2 + b^2)` to determine the length of the third side, which is the magnitude.

To normalize a vector, we can divide x and y by the magnitude.

Instead of normalizing to 1, we can use `setMag()` to directly set a magnitude.
