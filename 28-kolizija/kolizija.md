# Kolizija

Prilikom sudara, dva tela deluju jedno na drugo. Nakon sudara, njihovo kretanje se menja.

we need to make a distinction between collision detection and collision response.

Physics engines usually works collision detection by creating a physical body, usually attached to a visual representation of it. This body has properties such as velocity, position, rotation, torque, etc., and also a physical shape.

Detekcija sudara kruga i kocke i slično:
https://developer.mozilla.org/en-US/docs/Games/Techniques/3D_collision_detection

## Collision detection

Collision detection is a computational geometry problem involving the determination of whether and where two or more objects have collided.

![kolizija-kruznica](slike/kolizija-kruznica.png?row=true)

![kolizija-cilindar](slike/kolizija-cilindar.png?row=true)

Because the collision geometry and visible geometry are usually different, make collision a little smaller than the visible. The objects won’t get stuck so much, or appear to hit something that isn’t there.

## Collision response

Collision response coming after a collision is detected. Collision response is a kinetics problem involving the motion of two or more objects after they have collided.

![odbijanje-o-zid](slike/odbijanje-o-zid.png?row=true)

Restitution is the amount of bounce that an object has when it hits something. A good way to think of this is how high a ball will bounce when you drop it. If the restitution is 0.0f, when it hits it will simply stick to the ground. If you’ve got something like 0.99f, you’ve got a nice superball that will bounce around for a long time.

## Ugaoni efekat (Angular effects)

Including angular effects will yield more realistic collision responses for these rigid bodies.

![kolizija-ugaona](slike/kolizija-ugaona.png?row=true)

## Collision System

Any collision system worth its salt should be able to do a few basic things: report collision events, perform raycasts and shapecasts, and handle phantom objects.

A collision event should give you at a very minimum the following data: the two objects that collided, the sum normal of the collision, and the force of the collision.

Sort objects into collision groups: It optimizes the entire collision system. For example, objects like a bunch of crates on the first floor can’t collide with another group of crates on the second floor if they are physically separated by something like an elevator.

## Odbijanje vektora (vector reflection)

The simplest type of collision to model is one in which a moving object collides with a stationary object (kao kada lopta udari u zid). This type of scenario can be modeled using vector reflection. An interesting symmetry exists: The angle that the ball comes in at must equal the angle at which it leaves.

![odbijanje-vektora](slike/refleksija-vektora.png?row=true)

Ako je zid uspravan, all you have to do is reverse the horizontal component of the velocity when the ball hits. Similarly, if the wall is horizontal, all you have to do is reverse the direction of the vertical component of the ball's velocity.

(samo se obrne dx ili dy)

![odbijanje-vektora](slike/refleksija-vektora2.png?row=true)

If the stationary boundary is vertical: `vf = [–vix viy]`

if the stationary boundary is horizontal: `vf = [vix –viy]`

for incoming velocity vi = [vix viy].

Možemo koristiti sledeću funkciju:

```java
vector2D axisAlignedCollision(vector2D vect, char b)
{
  vector2D temp = vect;
  if (b == 'v')
    return temp.x *= -1;
  else if (b =='h')
    return temp.y *= -1;
}
```

Ako zid nije uspravan ni horizontalan, the first thing you need to find is the normal (N) to the line of the stationary object. The slopes are negative reciprocals of each other. So if the slope of the boundary line (B) is Dy/Dx, the slope of the normal (N) must be –Dx/Dy.

https://gamedevelopment.tutsplus.com/tutorials/basic-2d-platformer-physics-part-1--cms-25799

https://gamedevelopment.tutsplus.com/tutorials/basic-platformer-physics-part-5-object-vs-object-collision-detection--cms-27594
