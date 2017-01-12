## Collision detection

Collision detection is a computational geometry problem involving the determination of whether and where two or more objects have collided.

Physics engines usually works collision detection by creating a physical body, usually attached to a visual representation of it. This body has properties such as velocity, position, rotation, torque, etc., and also a physical shape.

![kolizija-cilindar](slike/kolizija-cilindar.png?row=true)

Because the collision geometry and visible geometry are usually different, make collision a little smaller than the visible. The objects won’t get stuck so much, or appear to hit something that isn’t there.

### Detekcija kolizije krugom

Krug se koristi u detekciji kolizije tako što se centar kruga postavi u centar predmeta, pa se meri rastojanje poluprečnikom. Ova metoda je neprecizna i ne odgovara za sve predmete.

![kolizija-kruznica](slike/kolizija-kruznica.png?row=true)

![circle_collide](slike/circle_collide.png?row=true)

![kolizija-krug](slike/kolizija-krug.png?row=true)

You can extend this process to 3D.

https://developer.mozilla.org/en-US/docs/Games/Techniques/3D_collision_detection
