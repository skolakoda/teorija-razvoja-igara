# Sabiranje i oduzimanje vektora

Vektori su mogu sabirati prema pravilima linearne algebre.

## Sabiranje vektora

![vector_addition](slike/vector_addition.png?row=true)

Think of vector addition as displacement on a road map. If you travel along vector `v` and then turn and follow vector `w`, you really go from the beginning of `v` to the end of `w`.

Sabiranjem vektora izračunavamo ukupnu silu (rezultantu) koja deluje na neki predmet:

![sabiranje-vektora](slike/sabiranje-vektora.png?row=true)

![vector-airplane](slike/vector-airplane.gif?row=true)

Sabiranje 3D vektora:
```
a + b = [ (a x + b x ), (a y + b y ), (a z + b z ) ]
```

## Oduzimanje vektora

We can also subtract one vector from another:
* first we reverse the direction of the vector we want to subtract,
* then add them as usual:

![vector-subtract](slike/vector-subtract.gif?row=true)

Vector subtraction `a – b` is nothing more than addition of `a` and `–b`:
```
a – b = [ (a x – b x ), (a y – b y ), (a z – b z ) ]
```
