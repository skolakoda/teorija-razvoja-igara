# Projekcija

A projection is a way to transform a world from one dimensionality to another.

Finite projections only project objects onto a finite space of the lower dimensionality. For a 3D to 2D projection, there is a finite plane on which the world is projected. For 2D to 1D, there is a bounded line that is the result of the projection.

# 3D projekcija
> Projektovanje možemo zamisliti kao bacanje senke

3D projekcija je mapiranje trodimenzionalnog prostora na dvodimenzionalnu ravan (It's like taking a photo). Svet je trodimenzionalan, ali ekran na kome ga prikazujemo je uvek 2D.

Proces:
* define 3D coordinates in code
* transform 3D coordinates into 2D ones (transformations of vertex positions)
* render 2D coordinates on screen

![3d-projekcija](slike/3d-projekcija.jpg)

The 3D to 2D projection is an abstract math operation, usually made by the camera object.

# Ortografska (paralelna) projekcija

An orthographic projection is a very simplistic projection. When projecting onto an axis-aligned surface, the projection simply throw away the coordinate perpendicular to the surface.

Na slici je prikazana 2D to 1D Orthographic Projection:

![](slike/Ortho2DProjection.svg)

A simple orthographic projection onto the plane z = 0 can be defined by the following matrix:
```
[ 1 0 0
  0 1 0
  0 0 1 ]
```

Often, it is more useful to use homogeneous coordinates. The transformation above can be represented for homogeneous coordinates as:
```
[ 1 0 0 0
  0 1 0 0
  0 0 1 0
  0 0 0 1 ]
```

Human eyes do not see the world via orthographic projection.

# Perspektivna projekcija

> The farther an object is from the camera, the smaller it appears in the final image. It's similar to how our eye works.

Unlike the above projection type, perspective projection relies on the concept of a focal point.

A perspective projection is a projection of the world on a surface as though seen through a single point. A 2D to 1D perspective projection looks like this:

![](slike/Persp2DProjection.svg)

An orthographic projection only captures the rectangular prism directly in front of the surface of projection. A perspective projection captures a larger space of the world.

In 2D, the shape of the perspective projection is a regular trapezoid (a quadrilateral that has only one pair of parallel sides, and the other pair of sides have the same slope). In 3D, the shape is called a frustum; essentially, a pyramid with the tip chopped off.

![](slike/ViewFrustum.svg)

The viewing volume for a 3D perspective projection is a frustum of a pyramid, a truncated pyramid whose top has been cut off by a plane parallel to its base.

![perspektiva](slike/perspektiva.png)

# Računanje perspektive


# Primena

You start with coordinates in 3D space (space_x, space_y and space_z) and you want to turn them into coordinates on the screen (screen_x and screen_y). That means you have to make one number disappear, namely space_z. How can you do that? By dividing everything by space_z!

```
screen_x = space_x / space_z
screen_y = space_y / spaze_z
```


Poseban repo:
https://github.com/skolakoda/ucimo-3d-projekciju

Linkovi:
http://alfonse.bitbucket.org/oldtut/Positioning/Tut04%20Perspective%20Projection.html
http://ogldev.atspace.co.uk/www/tutorial12/tutorial12.html
