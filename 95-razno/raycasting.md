## Raycasting

Raycasting is both a savior and a curse. It stabs a ray from a start location in your game world to any other point and gives you the collision information for anything it intersects along the way. This is really useful for detecting line of sight from an AI creature to your player’s character.

The problem with raycasting is that it’s only accurate to a point. If you want to know if your character is standing next to an open window, you can make a few rays, but they might miss something important, such as bars over the windows.

It can get expensive fast, though. Raycasts can be pretty expensive, especially if you want a list of objects sorted by distance. A good trick is to cache the results of multiple raycasts over many game loops. If you cast one ray per loop from an AI character, and your game is running at 30Hz, that’s 30 rays per second you can cast!

Another option is the shapecast. Think of this as pushing a geometrical shape from a start location in your game world along a straight line to somewhere else.
