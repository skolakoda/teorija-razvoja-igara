## Množenje vektora i skalara

When you multiply a scalar by the vector, you're actually scaling its magnitude, while leaving its direction unchanged.

Multiplication of a vector `a` by a scalar `s` is accomplished by multiplying the individual components of `a` by `s`:
```
s * a = ( s * ax, s * ay, s * az)
```

## Skalarni proizvod vektora (*dot product*)

Skalarni proizvod vektora (engleski *dot product*, jer se piše pomoću tačke) is an operation that, given two vectors, returns a floating-point value. It is usually depicted as:
```
u • v
```
It is computed as follows:
```
ux*vx + uy*vy + uz*vz
```
Dot products can be computed on any vectors, but usually on normalized vectors. When applied to unit vectors, the dot product can be interpreted as the cosine of the angle between the two vectors being multiplied. Thus, the dot product of two parallel vectors equals one, and the dot product of two perpendicular vectors equals zero.

## Vektorski proizvod (*cross product*)

Vektorski proizvod (engleski *cross product*, jer se piše pomoću krstića tj. `x`) is an operation that, given two vectors, returns a third vector. It is usually expressed as:
```
u * v
```
the preceding equation can be expressed as:

```
[uy*vz - uz*vy, uz*vx - ux*vz, ux*vy - uy*vx]
```
But notice how cross products are more expensive to compute than the dot version.

![cross-product](slike/cross-product.gif?row=true)
