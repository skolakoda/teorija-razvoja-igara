# Vektori

Vektor je veličina koja ima intenzitet i smer.

A vector can be visualized as a directed line segment, extending from the tail to the head. A vector is "carried" the point A to the point B; the Latin word vector means "carrier". Vectors entered math in the 19 century, as mathematicians and physicists wrestled to describe motion, rather than static position.

![vektori](slike/vectori.png?row=true)

There are no built-in data types for storing vectors. Vectors can be coded as an array of numbers or as a user-defined structure.

```c
struct 3Dvector
{
  float x, y, z;
};
```

It is possible to create an extremely powerful structure or class which can encompass almost every operation which could be needed.

## Skalari

Scalars are any quantity that can be measured using a number (temperature, length, mass...). It have magnitude but no direction.

## Vector vs. Scalar

The difference between vectors and scalars lies in the direction.

For example, suppose your friend is having car trouble, and he calls and asks you to come pick him up because he's only 2 miles away. You say no problem and hop in your car. But how will you find him? If he had said 2 miles due east on your street, you might have had a better chance of locating him. That's the difference between vectors and scalars.

## Coordinate system

In one dimension there are only two possible directions, positive or negative. In 2D, positive or negative isn't enough.

There are two ways for describing a vector in 2D: polar coordinates and Cartesian coordinates. Polar coordinates describe its length and direction, Cartesian coordinates describe its horizontal and vertical displacement.

## Magnitude

The magnitude of a vector is a scalar representing the length of the vector. We can use the Pythagorean theorem to calculate a vector’s magnitude.

![vector-magnitude](slike/vector-magnitude.jpg?row=true)

## Jedinični vektor (normalizacija vektora)

A unit vector is a vector with a magnitude of one. We can convert any vector to a unit vector that points in the same direction, but has unit length.

X-axis of unit vector is typically called `i`, y-axis is `j`, and z-axis is `k`.

## Normal Vectors

A vector is said to be normal to a surface if it is perpendicular to it. Be careful not to confuse the term “normalization” with the term “normal vector.”

## Sabiranje i oduzimanje vektora

Vektori su mogu sabirati prema pravilima linearne algebre.

Think of vector addition bellow as displacement on a road map. If you travel along vector `v` and then turn and follow vector `w`, you really go from the beginning of `v` to the end of `w`.

![vector_addition](slike/vector_addition.png?row=true)

We can also subtract one vector from another:
* first we reverse the direction of the vector we want to subtract,
* then add them as usual:

![vector-subtract](slike/vector-subtract.gif?row=true)

![sabiranje-vektora](slike/sabiranje-vektora.png?row=true)

![vector-airplane](slike/vector-airplane.gif?row=true)

```
a + b = [ (a x + b x ), (a y + b y ), (a z + b z ) ]
```

Vector subtraction `a – b` is nothing more than addition of `a` and `–b`:
```
a – b = [ (a x – b x ), (a y – b y ), (a z – b z ) ]
```

## Množenje vektora

When you multiply a scalar by the vector, you're actually scaling its magnitude, while leaving its direction unchanged.

Multiplication of a vector `a` by a scalar s is accomplished by multiplying the individual components of `a` by `s`:
```
s * a = ( s * ax, s * ay, s * az)
```

## Dot Product

The dot product is an operation that, given two vectors, returns a floating-point value. It is usually depicted as:
```
u • v
```
It is computed as follows:
```
ux*vx + uy*vy + uz*vz
```
Dot products can be computed on any vectors, but usually on normalized vectors. When applied to unit vectors, the dot product can be interpreted as the cosine of the angle between the two vectors being multiplied. Thus, the dot product of two parallel vectors equals one, and the dot product of two perpendicular vectors equals zero.

## Cross Product

The cross product is an operation that, given two vectors, returns a third vector. It is usually expressed as:
```
u * v
```
the preceding equation can be expressed as:

```
[uy*vz - uz*vy, uz*vx - ux*vz, ux*vy - uy*vx]
```
But notice how cross products are more expensive to compute than the dot version.

![cross-product](slike/cross-product.gif?row=true)

## Vector unit circle

Dot proizvod dva normalizovana 2D vektora od kojih je jedan jedinični vektor (1, 0) je uvek x komponenta drugog. Na primer:
```
(0.8, 0.6) * (1, 0) = 0.8 * 1 + 0.6 * 0 = 0.8 + 0 = 0.8
```

Na kraju dobijamo neku vrstu jediničnog kruga, gde je dot proizvod zapravo kosinus.

![vector-unit-circle](slike/vector-unit-circle.png?row=true)

## Direction Inversion

Geometrically, direction Inversion of the vector is very simple. Just switch the tail and the head.

If you think of vectors in terms of Cartesian coordinates, inverting is a simple matter of swapping the two coordinates — which is the same as multiplying everything by Ϫ1.

## Trigonometrijske funkcije

The sine can be used to calculate the y-coordinate of a vector, and the cosine can be used to calculate the x-coordinate. The sin() and cos() functions take the angle, and return a number between -1 and 1. If you multiply this number by the length of the vector, you will get the exact Cartesian coordinates of the vector:
```
speed_x = speed * cos(angle);
speed_y = speed * sin(angle);
```

http://alfonse.bitbucket.org/oldtut/Basics/Introduction.html
