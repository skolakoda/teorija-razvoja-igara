# Sudar (*kolizija*)

Prilikom sudara, dva tela deluju jedno na drugo. Nakon sudara, njihovo kretanje se menja.

we need to make a distinction between collision detection and collision response.

## Sistem sudara

Any collision system should be able to do a few basic things: report collision events, perform raycasts and shapecasts, and handle phantom objects.

A collision event should give you at a very minimum the following data: the two objects that collided, the sum normal of the collision, and the force of the collision.

Sort objects into collision groups: It optimizes the entire collision system. For example, objects like a bunch of crates on the first floor can’t collide with another group of crates on the second floor if they are physically separated by something like an elevator.

## Primena

Prilikom sudara različitih tela, na osnovu tipa tela se poziva odgovarajuća funkcija. U pseudokodu:
```java
collisionCallbackArray = {
  AABBvsAABB
  AABBvsCircle
  CirclevsAABB
  CirclevsCircle
}

// type can be of either AABB or Circle
collisionCallbackArray[A->type][B->type](A, B)
```

https://gamedevelopment.tutsplus.com/tutorials/basic-2d-platformer-physics-part-1--cms-25799

https://gamedevelopment.tutsplus.com/tutorials/basic-platformer-physics-part-5-object-vs-object-collision-detection--cms-27594
