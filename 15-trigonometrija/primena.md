#  Primena trigonometrijskih funkcija

## Visina drveta

![trigonometrija-uzivo](slike/trigonometrija-uzivo.jpg)

## Širina reke

![sirina-reke](slike/sirina-reke.gif)

## Crtanje kruga

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

## Kruženje nebeskih tela

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

## Prateća raketa

Suppose you are writing a game in which the player can fire homing missiles. First you calculate the direction of the target, as seen from the missile. You can visualize it as a vector. The x- and y-coordinates of this vector can be calculated easily - just subtract the coordinates of the missile from the coordinates of the target.

Given the x- and y-coordinates of the vector, you can calculate its angle and length, using the atan:
```
target_angle = atan2 (target_y - y, target_x - x)
```
