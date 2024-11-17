## Množenje vektora i skalara (skaliranje vektora)

Kada množimo skalar sa vektorom, zapravo skaliramo njegovu dužinu, dok smer ostaje nepromenjen.

Množenje vektora `v` skalarom `s` vršimo tako što sve pojedinačne komponente vektora množimo skalarom:

```js
s * v = (s * v.x, s * v.y, s * v.z)
```

U kodu:

```js
function skaliraj(v, s) {
  return {
    x: v.x * s,
    y: v.y * s,
    z: v.z * s
  }
}
```

Skaliranjem sa -1 vektor obrće smer, odnosno menja glavu i rep. Na primer:

\(\vec{v} = (3, -2, 5)\)

pomnožen sa -1 postaje:  

\(-\vec{v} = (-3, 2, -5)\)  

### Skaliranje vektora u igrama

U igrama često množimo vektor skalarom. Na primer, možemo simulirati otpor vazduha množeći brzinu igrača sa 0.9 pri svakom kadru.

## Skalarni proizvod (dot proizvod)

Skalarni proizvod vektora ili dot proizvod (*dot product*) je operacija koja za množenje dva vektora vraća realnu vrednost. Piše se pomoću tačke:  

\[
\vec{u} \cdot \vec{v}
\]  

Računa se na sledeći način:

```js
u.x * v.x + u.y * v.y + u.z * v.z
```

Skalarni proizvod dva jedinična vektora daje kosinus ugla između njih. Ako su vektori paralelni, \(\cos(0^\circ) = 1\), a ako su vektori ortogonalni, \(\cos(90^\circ) = 0\).

![](slike/dotsimple.jpg)

Kao što vidimo, kada vektori pokazuju u istom smeru, dot proizvod je pozitivan, kada su okomiti je  nula, a kada su suprotnog smera negativan. Dakle, dot proizvod je proporcionalan tome koliko se smer vektora poklapa.

### Dot proizvod u igrama

Recimo da imamo stražara na poziciji `G` (1,3) koji gleda u smeru `D` (1,1), sa vidnim poljem od 180 stepeni. Imamo heroja koji se šunja na poziciji `H` (3,2). Je li on u vidnom polju stražara? 

Da bismo to otkrili, prvo računamo vektor smera `V` od stražara do heroja:

```
V = H-G = (3,2)-(1,3) 
        = (3-1, 2-3) 
        = (2, -1)
```

Konačno, računamo skalarni proizvod vektora `D` (pogled stražara) i `V` (smer od stražara ka heroju), da saznamo njihovo poklapanje:

```
D•V = (1,1)•(2,-1) = 1*2+1*-1 = 2-1 = 1
```

Pošto je rezultat pozitivan, heroj je u vidnom polju stražara!

## Vektorski proizvod (*cross product*)

Vektorski proizvod (engleski *cross product*, jer se piše pomoću krstića tj. `x`) is an operation that, given two vectors, returns a third vector:
```
u * v
[uy*vz - uz*vy, uz*vx - ux*vz, ux*vy - uy*vx]
```
But notice how cross products are more expensive to compute than the dot version.

![cross-product](slike/cross-product.gif)

Let's say you have a boat that has cannons that fire to the left and right. Given that the boat is facing along the direction vector (2,1), in which directions do the cannons fire? This is easy in 2D: to rotate 90 degrees clockwise, just flip the two vector components, and then switch the sign of the second component. (a,b) becomes (b,-a). So, if the boat is facing along (2,1), the right-facing cannons fire towards (1,-2). The left-facing cannons fire in the opposite direction, so we flip both signs to get: (-1,2).

![cross-product](slike/boat-3.jpg)

So, what if we want to do this in 3D? Let's revisit our sailing ship. We have a vector for the direction of the mast M, going straight up (0,1,0), and the direction of the north-north-east wind W (1,0,2), and we want to find the direction the sail S should stick out in order to best catch the wind. The sail has to be perpendicular to the mast, and also perpendicular to the wind. To solve this, we can use the cross product: S = M x W.

![cross-product](slike/boat2.jpg)

The cross product of A(a1,a2,a3)) and B(b1,b2,b3)) is:
(a2b3-a3b2, a3b1-a1b3, a1b2-a2b1)

So now we can plug in our numbers and solve our problem:

S = MxW = (0,1,0)x(1,0,2) = ([1*2-0*0], [0*1-0*2], [0*0-1*1]) = (2,0,-1)

This is pretty ugly to do by hand. For most graphics and game work I would recommend just encapsulating it in a function like the one below, and never thinking about the details again.

```java
vec3 cross(vec3 a, vec3 b) {
    vec3 result;
    result[0] = a[1] * b[2] - a[2] * b[1];
    result[1] = a[2] * b[0] - a[0] * b[2];
    result[2] = a[0] * b[1] - a[1] * b[0];
    return result;
}
```

## 2D vektorski proizvod (*cross product*)

The 2D cross product, unlike the 3D version, does not return a vector but a scalar. This scalar value actually represents the magnitude of the orthogonal vector along the z-axis, if the cross product were to actually be performed in 3D. In a way, the 2D cross product is just a simplified version of the 3D cross product. But, the order of operations is important: a×b is not the same as b×a.

Two vectors can be crossed, a scalar can be crossed with a vector, and a vector can be crossed with a scalar. Here are the operations:

```cpp
// Two crossed vectors return a scalar
float CrossProduct(const Vec2& a, const Vec2& b)
{
  return a.x * b.y - a.y * b.x;
}

// cross product with a vector a and scalar s, both returning a vector
Vec2 CrossProduct(const Vec2& a, float s)
{
  return Vec2( s * a.y, -s * a.x );
}

Vec2 CrossProduct(float s, const Vec2& a)
{
  return Vec2( -s * a.y, s * a.x );
}
```

http://gafferongames.com/game-physics/physics-in-3d/
