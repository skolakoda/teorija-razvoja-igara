# Hijerarhija klasa: Keep Them Flat

![nasledjivanje-klasa](slike/nasledjivanje.png)

A good rule of thumb is that each class should have a single responsibility in your code base and should have inheritance trees that are no more than two or three levels deep.

If at all possible, try to never use multiple inheritance unless every base class you’re deriving from has nothing but pure virtual functions.

Eventually, you’d probably end up with a big inheritance tree like this one:

![hijerarhija](slike/hijerarhija.png)

## Inheritance vs. Composition

Inheritance is used when an object has evolved from another object, or when a child object is a version of the parent object. Composition is used when an object is composed of multiple discrete components, or when an aggregate object has a version of the contained object.

![sistem-komponenti](slike/sistem-komponenti.png)

Converting “is-a” relationships into “has-a” relationships can be a useful technique for reducing the width, depth, and complexity of a game’s class hierarchy.
