# Linija

Za početak, potrebno nam je da savladamo osnovnu terminologiju na srpskom i engleskom:

* Linija ili prava (*line*) je neograničena prava linija
* Poluprava ili zrak (*ray*) je prava linija ograničena tačkom sa jedne strane
* Duž (*line segment*) je prava linija ograničena tačkama sa obe strane

## Vrh (*vertex*)

Tačka u 3D koordinatnom sistemu zove se vrh (*vertex*). Svaki vrh u 3D grafici ima sledeće atribute:

* Position: Identifies it in a 3D space (x, y, z).
* Color: Holds an RGBA value (all values range from 0.0 to 1.0).
* Normal: A way to describe the direction the vertex is facing.
* Texture: A 2D image that the vertex can use to decorate the surface it is part of instead of a simple color.

## Lice (*face*)

Lice je ravan između vrhova. For example, a cube has 8 different vertices (points in space) and 6 different faces, each constructed out of 4 vertices. A normal defines which way the face is directed in. Also, by connecting the points we're creating the edges of the cube. The geometry is built from a vertex and the face, while material is a texture, which uses a color or an image. If we connect the geometry with the material we will get a mesh.

![](slike/3d-cube.png)
