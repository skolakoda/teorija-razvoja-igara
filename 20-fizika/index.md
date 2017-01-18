# Fizika

The great thing about modeling physics is this: if you model the forces correctly, you’ll get objects that behave realistically.

The major components of a physics engine include:
• Physics models
• Simulated objects manager
• Collision detection engine
• Collision response module
• Force effectors
• Numerical integrator
• Game engine interface

A rigid body is just a shape defined by the developer that is implicitly defined to be non-deformable.

## Jedinice i mere

Units of measure don’t matter in any physics calculation. All the formulas will work, as long as you are consistent. A measure of distance can therefore be anything you like: meters, feet, inches, and so on.

## Fizički pogon

Ako se vaša igra zasniva na fizici, potrebno je da fizički pogon:
* pravi fizički predmet za predmete igre
* ažurira fiziku za svaki kadar
* otkriva i odgovara na sudare
* vraća ažurirane informacije o položaju za svaki kadar

Neki od postojećih fizičkih pogona su:
* [Box2d](http://www.box2dflash.org/docs/2.0.2/manual) (korišten i za Angry Birds)

Developing a robust physics engine is difficult, but in some cases, building a simple physics engine is a good choice.

https://gamedevelopment.tutsplus.com/articles/whats-in-a-projectile-physics-engine--cms-21584

https://gamedevelopment.tutsplus.com/series/how-to-create-a-custom-physics-engine--gamedev-12715
