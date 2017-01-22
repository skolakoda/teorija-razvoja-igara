# Fizika

The great thing about modeling physics is this: if you model the forces correctly, you’ll get objects that behave realistically. Glavne sile prirode su gravitacija i otpor okruženja: trenje (po tlu) i vučenje (kroz vodu i vazduh).

Units of measure don’t matter in any physics calculation. All the formulas will work, as long as you are consistent.

A rigid body is a shape defined by the developer that is implicitly defined to be non-deformable.

## Fizički pogon

Developing a robust physics engine is difficult, but in some cases, building a simple physics engine is a good choice.

A physics engine helps us do two very important things for our game:
* detect collisions between game objects
* simulate the forces and resulting motion of our objects from those collisions

Fizički pogon to radi na sledeći način:
* pravi fizički predmet za predmete igre
* ažurira fiziku za svaki kadar
* otkriva i odgovara na sudare
* vraća izračunate podatke o položaju za svaki kadar

The major components of a physics engine include:
• Physics models
• Simulated objects manager
• Collision detection engine
• Collision response module
• Force effectors
• Numerical integrator
• Game engine interface

https://gamedevelopment.tutsplus.com/articles/whats-in-a-projectile-physics-engine--cms-21584

https://gamedevelopment.tutsplus.com/series/how-to-create-a-custom-physics-engine--gamedev-12715
