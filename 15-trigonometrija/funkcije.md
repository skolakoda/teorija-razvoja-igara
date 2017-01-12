# Trigonometrijske funkcije

The trigonometric functions are relationships between two sides of a right triangle. Any time we have a scenario with a right triangle, the trig functions come in handy. We'll also use them in the vectors and in physics.

The most familiar trigonometric functions are the sine, cosine, and tangent:
* sin = opposite / hypotenuse
* cos = adjacent / hypotenuse
* tan = opposite / adjacent
You can memorize them with SOH, CAH, TOA.

![trigonometrijske-funkcije](slike/trigonometrijske-funkcije.png?row=true)

## Sinus i kosinus

The sin() and cos() functions take only one parameter, the angle, and return a number between -1 and 1.

Sinusoidal graph pattern repeats every 360°; this is called the fundamental period. To change the period, just place a number in front of the x.

![sinus-kosinus-graf.png](slike/sinus-kosinus-graf.png?row=true)

C program prikazuje sinusnu funkciju:
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
