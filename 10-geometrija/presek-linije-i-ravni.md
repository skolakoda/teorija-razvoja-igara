## Line–plane intersection

Imagine a fast bullet and a collision detection with a relatively small target. Because the target is small and the bullet is incredibly fast, it could happen that on successive frames the bullet is on opposite sides of the target. No single frame exists where the bullet is actually inside the target.

The only way to find if the intersection happen is to test if the ray intersected the target.
