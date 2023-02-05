# Otkrivanje sudara složenih tela

There are two predominant collision detection methods za konveksne figure:
* The [separating axis theorem](https://en.wikipedia.org/wiki/Hyperplane_separation_theorem) is widely used for 2D collision detection.
* [GJK distance algorithm](https://en.wikipedia.org/wiki/Gilbert%E2%80%93Johnson%E2%80%93Keerthi_distance_algorithm) is more commonly used for 3D collision detection, because the separating axis algorithm is expensive when done in 3D.
