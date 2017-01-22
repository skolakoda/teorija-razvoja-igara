# Fizički pogon

Physics simulation is called within the loop of your game scene.

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
