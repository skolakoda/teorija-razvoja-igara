# Fizički predmet

Fizički predmet contains all information about physics. It will store the oblik that the object is represented by, mass data, transformation (position, rotation), brzina, torque, and so on. Here is what our body ought to look like:

```java
struct body
{
  Oblik *oblik;
  Transform tx;
  Material materijal;
  MassData masa;
  Vector sila;
  Vector brzina;
}
```

## Oblik

There are some intelligent decisions made here that tend towards  code organization. A oblik is contained within the body by means of a pointer. This represents a loose relationship between the body and its oblik. A body can contain any oblik, and the oblik can be swapped around at will (npr. možemo zameniti geometriju za sudare). In fact, a body can be represented by multiple obliks, and such a body would be known as a "composite".

## Masa

`masa` is a small data structure to contain mass-related information:
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

It is nice to store all mass- and intertia-related values in a single structure. The mass should never be set by hand - mass should always be calculated by the oblik itself:

```java
Mass = density ∗ volume
```

Whenever you want a oblik to be more "massive" or "heavy", you should modify the density of a oblik. This is the proper way to go about the situation, as density is not affected by volume and will never change during the runtime of the game.

## Materijal

But where does the density value lay? It resides within the Material structure:
```java
struct Material
{
  float density;
  float restitution;
};
```
Some useful materijal settings for common materijal types can be used to construct a Material object from an enumeration value:
```
Rock       Density : 0.6  Restitution : 0.1
Wood       Density : 0.3  Restitution : 0.2
Metal      Density : 1.2  Restitution : 0.05
BouncyBall Density : 0.3  Restitution : 0.8
SuperBall  Density : 0.3  Restitution : 0.95
Pillow     Density : 0.1  Restitution : 0.2
Static     Density : 0.0  Restitution : 0.4
```

## Sila

`sila` value starts at zero at the beginning of each physics update. Other influences in the physics engine (such as gravity) will add vectors into this sila data member. Just before integration all of this sila will be used to calculate acceleration of the body. After integration the sila is zeroed out.

This allows for any number of silas to act upon an object whenever they see fit, and no extra code will be required to be written when new types of silas are to be applied to objects.
