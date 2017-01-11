## Mapping

Mapping is a compression technique that will allow us to create good-looking game worlds at a fraction of the memory footprint. Mapping was used in thousands of classic games, and is still used today, even in some 3D games. The key idea is to divide our game world into a set of tiles or basic primitives. Each tile is a rectangular pattern, which we will combine with other tiles to represent the level.

The compression comes from the fact that, if we repeat the same pattern frequently, we will only have it once in memory.
