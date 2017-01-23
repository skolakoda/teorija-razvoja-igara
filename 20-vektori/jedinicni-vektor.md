## Normalizacija vektora (jedinični vektor)

A unit vector is a vector with a length of 1. We can convert any vector to a unit vector that points in the same direction, but has unit length.

To normalize a vector, divide each component by the vector's length:
```
jedinicni_vektor = (vektor.x, vektor.y, vektor.z) / duzina_vektora
```

If we want to normalize vector (3,4), we divide each component by its length, 5, to get (3/5, 4/5).

Postoji i drugi način:
```
jedinicni_vektor = 1 / duzina_vektora * vektor
```

X-axis of unit vector is typically called `i`, y-axis is `j`, and z-axis is `k`.

In games, when we are dealing with directions (as opposed to positions or velocities), it is important that they have unit length. For example, let's say there is a gun pointing in the direction of (1,0) that shoots a bullet at 20 m/s. What is the velocity of the bullet? Since the direction has length 1, we can just multiply the direction and the bullet speed to get the bullet velocity: (20,0).
