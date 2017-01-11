## Transformacije

Transformations is really just a fancy word for moving objects around in your world. It encompasses movement such as forward and backward or up and down motion, scaling objects larger or smaller, and even rotating objects.

### Translacija

Suppose you had an object at point P(1,2) and you wanted to move it three units to the right and one unit up. Well, if you add 3 to the x-coordinate and 1 to the y-coordinate, the object would end up three units to the right and one unit up. That gives you a new location of (1+3,2+1) = (4,3).

That approach is simple if you're translating only one point or even just a few points. However, most models in games are defined by hundreds, if not thousands, of points, so you need a more systematic way of adding 3 to every x and 1 to every y. You could set up a loop and perform the following on each point.

Remember that when adding matrices you just add corresponding entries.

Translation by addition is pretty straightforward. Here is an example of how to translate a 3D point using addition:

```java
Matrix3X1 translate3DByAddition(Matrix3X1 start, Matrix3X1 trans)
{
  Matrix3X1 temp;
  temp = addMatrices(start,trans);
  return temp;
}
```

### Množenje

If you plan to scale or rotate the object, you need to use matrix multiplication. Also, take note of the order in which the matrices are multiplied.

### Skaliranje

The process is the same as translation: Plug in each vertex one at a time, and multiply the matrices to find its new location. If you want to perform a uniform (proportional) scale, just make sure that Sx = Sy. If you plug in two different values for Sx and Sy, you'll end up with a differential scale.

The scaling process works the exact same way in 3D.

![skaliranje](slike/skaliranje.png?row=true)

### Rotacija

There are actually two different approaches to rotating objects. One method uses quaternions, but the math is complex. This second method is Euler rotation. It is very similar to scaling and translating.

By default, the rotation matrix rotates objects with respect to the origin, just like the scaling matrix does. The resulting effect is that the object appears to be orbiting about the origin.
