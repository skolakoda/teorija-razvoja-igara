# Predmet (*GameObject, Actor, Entity*)

A game actor is an object that represents a single entity in your game world. Predmetu treba proslediti da li je statičan ili dinamičan, tj. da li je drvo ili reaguje na fiziku.

Između ostalog, Predmet contains all information about some given physics object. It will store the shape(s) that the object is represented by, mass data, transformation (position, rotation), velocity, torque, and so on. Here is what our body ought to look like:

```java
struct body
{
  Shape *shape;
  Transform tx;
  Material material;
  MassData mass_data;
  Vector force;
  Vector velocity;
};
```

## shape

There are some intelligent decisions made here that tend towards  code organization. A shape is contained within the body by means of a pointer. This represents a loose relationship between the body and its shape. A body can contain any shape, and the shape can be swapped around at will (npr. možemo zameniti geometriju za sudare). In fact, a body can be represented by multiple shapes, and such a body would be known as a "composite".

## mass_data

The mass_data is a small data structure to contain mass-related information:
```java
struct MassData
{
  float mass;
  float inv_mass;

  // for rotations
  float inertia;
  float inverse_inertia;
};
```

It is nice to store all mass- and intertia-related values in a single structure. The mass should never be set by hand - mass should always be calculated by the shape itself:

```java
Mass = density ∗ volume
```

Whenever you want a shape to be more "massive" or "heavy", you should modify the density of a shape. This is the proper way to go about the situation, as density is not affected by volume and will never change during the runtime of the game.

## material

But where does the density value lay? It resides within the Material structure:
```java
struct Material
{
  float density;
  float restitution;
};
```
Some useful material settings for common material types can be used to construct a Material object from an enumeration value:
```
Rock       Density : 0.6  Restitution : 0.1
Wood       Density : 0.3  Restitution : 0.2
Metal      Density : 1.2  Restitution : 0.05
BouncyBall Density : 0.3  Restitution : 0.8
SuperBall  Density : 0.3  Restitution : 0.95
Pillow     Density : 0.1  Restitution : 0.2
Static     Density : 0.0  Restitution : 0.4
```

## force

`force` value starts at zero at the beginning of each physics update. Other influences in the physics engine (such as gravity) will add vectors into this force data member. Just before integration all of this force will be used to calculate acceleration of the body. After integration the force is zeroed out.

This allows for any number of forces to act upon an object whenever they see fit, and no extra code will be required to be written when new types of forces are to be applied to objects.
