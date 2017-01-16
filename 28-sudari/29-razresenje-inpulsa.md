# Impulse Resolution

Impulse resolution is a particular type of collision resolution strategy. Collision resolution is the act of taking two objects who are found to be intersecting and modifying them in such a way as to not allow them to remain intersecting.

By resolving detected collisions we place a restriction upon movement such that objects cannot remain intersecting one another. The idea behind impulse resolution is to use an impulse (instantaneous change in velocity) to separate objects found colliding. In order to do this, the mass, position, and velocity of each object must be taken into account somehow: we want large objects colliding with smaller ones to move a little bit during collision, and to send the small objects flying away. We also want objects with infinite mass to not move at all.

# Problem zakucavanja

If the velocity is not big enough they will still collide after next update. This can cause objects to get stuck in each other.

## Rešenje 1

Daniel Kodicek (in his book, Mathematics & Physics for Programmers) does two things to achieve natural-looking collision resolution:

* His collision detection function calculates the exact time two objects will collide.
* He recalculates new velocities at the time of collision, so objects never overlap.

## Rešenje 2

Whenever two objects overlap, check if they are moving towards or away from each other. Do the collision only if they move towards each other.

It's pretty easy with vector math, simply calculate:

```java
dot_product(B.position - A.position, A.velocity - B.velocity)
```

If the result is positive the objects move towards each other.
