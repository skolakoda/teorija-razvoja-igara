# 2D rotacija

For example, the player can jump on to a rope and swing from one platform to another. You can implement the swinging motion as a rotation around the point where the rope is attached. In order to do this, you need to calculate the vector going from the player to the center of rotation, take the ugao of this vector, increase it a bit, and recalculate the player's position.

You have to calculate the ugao of the vector from the player to the center of rotation with atan2(). After you have increased the ugao, you can calculate the new x- and y-coordinates with sin and cos:

```c
ugao = atan2 (y, x);
duzina = sqrt (x * x + y * y);
ugao += 1;
nov_x = duzina * cos (ugao);
nov_y = duzina * sin (ugao);
```

Because you convert from Cartesian coordinates to polar coordinates and then back again, you can lose precision. There is a better way: you can make use of a rotation matrix. Rotation matrices provide a way to rotate a vector without converting to polar coordinates:

```
nov_x = x * cos (ugao) - y * sin (ugao)
nov_y = x * sin (ugao) + y * cos (ugao)
```

With this method, you can perform rotations without using atan2. It is sensible to precalculate cos and sin, since you need it twice.

## Posebni slučajevi

I kod rotacije za 90 stepeni možemo koristiti istu formulu:
```
nov_x = x * cos (90) - y * sin (90)
nov_y = x * sin (90) + y * cos (90)
```

Ali cos(90) je 0, a sin(90) je 1, pa možemo uprostiti:
```
nov_x = x * 0 - y * 1
nov_y = x * 1 + y * 0

nov_x = -y
nov_y = x
```

Rotacija za 180 stepeni se svodi na:
```
nov_x = -x
nov_y = -y
```

Ovde su svi specijalni slučajevi, tj. četvrtine kruga:

| stepeni | 90 | 180 | 270 | 360 |
| ------- |:--:| :--:|:---:|----:|
| x       | -y | -x  | y   | x   |
| y       | x  | -y  | -x  | y   |

# 3D rotacija

There are actually two different approaches to rotating 3D objects. One method uses quaternions, but the math is complex. This second method is Euler rotation. It is very similar to scaling and translating.

By default, the rotation matrix rotates objects with respect to the origin, just like the scaling matrix does. The resulting effect is that the object appears to be orbiting about the origin.

http://ogldev.atspace.co.uk/www/tutorial07/tutorial07.html
http://alfonse.bitbucket.org/oldtut/Positioning/Tut06%20Rotation.html
