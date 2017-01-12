# Proceduralne animacije

## Explicit vs Implicit Methods (Sprites vs Models)

Animation methods could be explicit or implicit. Explicit methods store the sequence of animation every few frames, like snapshots from a movie. It is memory intensive.

Implicit (procedural) animation methods do not store the animation data, but a higher level description of the motion. Skeletal animation systems, for example, store the configuration (in terms of its rotation angles) for each joint, like the elbow, knee, and so on. Then, in real time, this description is mapped to a character mesh, so the animation is computed. This computation usually involves complex math, thus, these methods are all fairly intensive for the CPU.

Advantage of procedural techniques is that they can be adapted to the scenario. Another benefit is data amplification: high-complexity results from relatively simple data input. A fractal terrain generator using midpoint displacement gets a quad as input, but can generate infinitely detailed mountains from it.

Vidi: proceduralno generisanje
