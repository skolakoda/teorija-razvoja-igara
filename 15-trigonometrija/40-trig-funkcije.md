# Trigonometrijske funkcije

Trigonometrijske funkcije, takođe poznate kao kružne funkcije, računaju nepoznati ugao pravouglog trougla pomoću dužine stranica. Ti uglovi mogu ići od 0 do 90 stepeni.

Koriste se i za krugove, jer oni imaju uglove, a u neku ruku i hipotenuzu (poluprečnik). Ugao unutar kruga može iznositi bilo koju pozitivnu ili negativnu vrednost (za razliku od pravouglog trougla).

Trigonometrijske funkcije su posebno bitne za razvoj igara. Koriste se za računanje rastojanja i ugla ka nekom predmetu, računanje vektora, simulaciju fizike, modelovanje kružnog kretanja, talasa i drugih periodičnih pojava.

Najpoznatije trigonometrijske funkcije su sinus, kosinus i tangent:
* sin = opposite / hypotenuse
* cos = adjacent / hypotenuse
* tan = opposite / adjacent
You can memorize them with SOH, CAH, TOA.

![trigonometrijske-funkcije](slike/trigonometrijske-funkcije.png)

## Sinus i kosinus

`sin()` i `cos()` funkcije primaju jedan parametar, ugao, i vraćaju broj između -1 i 1. Ugao može biti beskonačne veličine, ali se sinusoidni obrazac ponavlja svakih 360°, što se zove osnovni period. Da promeniš period, samo staviš broj (modifikator) ispred x.

![sinus-kosinus-graf.png](slike/sinus-kosinus-graf.png)

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

![](slike/sine.gif)

## Tangent

There is a mathematical function called the tangent, which can be used to calculate the ratio of `y` to `x`:
```
tan(angle) = y / x
```

![](slike/tan.gif)

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

![](slike/suprotni-vektori.gif)

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

https://jsfiddle.net/mudroljub/c10hjzqe/
