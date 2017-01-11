### Nedostaci matrica

A matrix is not always an ideal representation of a rotation, for a number of reasons:

1. We need nine floating-point values to represent a rotation, which seems excessive considering that we only have three degrees of freedom — pitch, yaw, and roll.

2. Rotating a vector requires a vector-matrix multiplication, which involves three dot products, or a total of nine multiplications and six additions.
We would like to find a rotational representation that is less expensive to calculate, if possible.

3. In games and computer graphics, it’s often important to be able to find rotations that are some percentage of the way between two known rotations. For example, if we are to smoothly animate a camera from some starting orientation A to some final orientation B over the course of a few seconds, we need to be able to find lots of intermediate rotations between A and B over the course of the animation. It turns out to be difficult to do this when the A and B orientations are expressed as matrices.

Thankfully, there is a rotational representation that overcomes these three problems. It is a mathematical object known as a quaternion.

### Kvaternion

A quaternion looks a lot like a four-dimensional vector, but it behaves quite differently. We usually write quaternions using non-italic, non-boldface type, like this:
```
q = [ qx qy qz qw ]
```

For our purposes, it will suffice to know that the unit-length quaternions (i.e., all quaternions obeying the constraint `qx^2 + qy^2 + qz^2 + qw^2 = 1`) represent three-dimensional rotations.

http://graphics.ucsd.edu/courses/cse169_w05/CSE169_04.ppt
