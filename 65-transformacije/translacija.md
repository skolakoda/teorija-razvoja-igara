# Translacija

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
