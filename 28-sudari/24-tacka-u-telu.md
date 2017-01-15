# Pripadnost tačke mnogouglu (*point inclusion tests*)

Pripadnost tačke mnogouglu je problem koji se često sreće u računarskoj grafici, a suština je određivanje da li se neka tačka nalazi na površini obuhvaćenoj mnogouglom. Point inclusion tests is essential for collision detection. From grenades to wall-following, almost every interesting algorithm needs to deal with this kind of issue.

## Tačka u sferi (3D)

The simplest point inclusion test involves testing whether a point is actually inside a sphere. Given the sphere:
```
(X-Xc)2 + (Y-Yc)2 + (Z-Zc)2 = R2
```
and the point P:
```
P=(px,py,pz)
```
P is inside the sphere only if:
```
(sqrt ( (px-xc)2 + (py-yc)2 + (pz-zc)2 ) < radius
```
Remember that square roots are expensive. Thus, an optimization could be:
```
( (px-xc)2 + (py-yc)2 + (pz-zc)2 ) < radius2
```
as well as storing the radius squared to speed up computations.

## Tačka u kutiji (3D)

Checking if a point is inside an AABB is pretty simple — we just need to check whether the point's coordinates fall inside the box, considering each axis separately. If we assume that Px, Py and Pz are the point's coordinates, and BminX – BmaxX, BminY – BmaxY, and BminZ – BmaxZ are the ranges of each exis of the 3D box, we can calculate whether a collision has occured:

```js
function isPointInsideBox(point, box) {
  return (point.x >= box.minX && point.x <= box.maxX) &&
         (point.y >= box.minY && point.y <= box.maxY) &&
         (point.z >= box.minY && point.z <= box.maxZ);
}
```

## Tačka u poligonu

The point-in-polygon problem asks whether a given point lies inside, outside, or on the boundary of a polygon. An early description of the problem in computer graphics shows two common approaches (ray casting and angle summation).

### Metoda zraka (ray casting)

Metod zraka polazi od činjenice da zrak pri svakom presecanju granice mnogougla ili ulazi ili izlazi iz njega:
* Neparan broj preseka: tačka je u mnogouglu
* Paran broj preseka: tačka je van mnogougla
Zrak može imati bilo koji smer, ali se zbog računanja uzimaju vektori paralelni sa x ili y-osom.

Jordan Curve Theorem states that a point is inside a 2D closed polygon only if the number of crossings from a ray emanating from the point in an arbitrary direction and the edges of the polygon is odd. The elegance of the Jordan Curve Theorem is that it only needs the polygon to be closed.

The algorithm can be described by the following pseudocode:

```py
bool isInside(point p, polygon P)
choose an arbitrary direction
build ray r based on p and the direction
initialize count to zero
for each edge
      test ray-segment
      if crossed
            increase count
      end if
end for
return count is odd
```

The algorithm price is O(n of edges), which is not too bad. The 2D Jordan Curve Theorem can be easily extended to 3D.
