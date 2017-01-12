# Trigonometrijske funkcije

The trigonometric functions are just relationships between two of the three sides of a right triangle. Any time we model a scenario with a right triangle, the trig functions come in handy. We'll also use them in the vectors and in physics.

The most familiar trigonometric functions are the sine, cosine, and tangent:
* sin = opposite / hypotenuse
* cos = adjacent / hypotenuse
* tan = opposite / adjacent
You can memorize them with SOH, CAH, TOA.

![trigonometrijske-funkcije](slike/trigonometrijske-funkcije.png?row=true)

![trigonometrija-uzivo](slike/trigonometrija-uzivo.jpg?row=true)

![sinus-kosinus-graf.png](slike/sinus-kosinus-graf.png?row=true)

Sinusoidal graph pattern repeats every 360°; this is called the fundamental period. To change the period, just place a number in front of the x.

Pomoću trigonometrijskih funkcija se može nacrtati i krug:
```js
draw_circle () {
    const length = 50;
    const angle_stepsize = 0.1;
    let angle = 0.0;

    while (angle < 2 * PI) {
      let x = length * cos(angle);
      let y = length * sin(angle);

      draw (x + SCREEN_W / 2, y + SCREEN_H / 2);
      angle += angle_stepsize;
  }
}
```

Prikazuje sinusnu funkciju:
```c
void draw_sine ()
{
    int length = 50;
    fixed x, y;
    fixed angle = 0;
    fixed angle_stepsize = itofix (5);
    // Allegro degrees range from 0 to 255
    while (fixtoi(angle) < 256)
    {
        // the angle is plotted along the x-axis
        x = angle;
        // the sine function is plotted along the y-axis
        y = length * fsin (angle);

        putpixel (screen,
            fixtoi (x), fixtoi (y) + SCREEN_H / 2,
            makecol (255, 255, 255));

        angle += angle_stepsize;
    }
}
```

![](slike/sine.gif?row=true)

With can use sin and cos to animate the orbit of a planet:

```c
void orbit ()
{
    int x = 0, y = 0;

    fixed angle = itofix (0);
    fixed angle_stepsize = itofix (1);

    // These determine the radius of the orbit.
    // See what happens if you change length_x to 100 :)
    int length_x = 50;
    int length_y = 50;

    // repeat this until a key is pressed
    while (!keypressed())
    {
        // erase the point from the old position
        putpixel (screen,
            fixtoi(x) + SCREEN_W / 2, fixtoi(y) + SCREEN_H / 2,
            makecol (0, 0, 0));

        // calculate the new position
        x = length_x * fcos (angle);
        y = length_y * fsin (angle);

        // draw the point in the new position
        putpixel (screen,
            fixtoi(x) + SCREEN_W / 2, fixtoi(y) + SCREEN_H / 2,
            makecol (255, 255, 255));

        // increment the angle so that the point moves around in circles
        angle += angle_stepsize;

        // make sure angle is in range
        angle &= 0xFFFFFF;

        // wait 10 milliseconds, or else it'd go too fast
        rest (10);
    }
}
```

## Tangent

There is a mathematical function called the tangent, which can be used to calculate the ratio of y to x:
```
tan(angle) = y / x
```

![](slike/tan.gif?row=true)

This can in fact be written as:

```
tan (angle) = sin (angle) / cos (angle)
```

This means the tan function is a combination of the sin and cos functions.

The inverse function of the tangent is called the arctangent:
```
angle = atan (y / x)
```

But there is a minor problem: this will sometimes give you an incorrect result. Two oposite vectors both have the same y-to-x ratio.

![](slike/suprotni-vektori.gif?row=true)

A partial work-around is possible like this (partial because we don't check for the case where x is 0):
```
if (x > 0)
    angle = atan (y / x);
else
    angle = PI + atan (y / x);
```
But to simplify things the function atan2() is available for programmers:

```
angle = atan2 (y / x)
```

## Prateća raketa

Suppose you are writing a game in which the player can fire homing missiles. First you calculate the direction of the target, as seen from the missile. You can visualize it as a vector. The x- and y-coordinates of this vector can be calculated easily - just subtract the coordinates of the missile from the coordinates of the target.

Given the x- and y-coordinates of the vector, you can calculate its angle and length, using the atan:
```
target_angle = atan2 (target_y - y, target_x - x)
```
