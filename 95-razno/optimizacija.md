# Optimizacija

Optimization can sometimes be difficult, but it is definitely one of the most exciting areas in game development. With some careful planning, lots of coffee, and patience, you can dramatically improve code performance.

My first suggestion is to use monitoring and create a statistical chart of where time is being spent. Identify major subsystems and assign a percentage of CPU time to them. These will include collision detection, AI, network (for multiplayer titles), sound, input processing, and so on. Focus on those subsystems that show the greatest potential.

## Ucitavanje resursa

Prvo glavni meni iz HTML-a, a zatim nivo na klik:
https://classroom.udacity.com/courses/cs255/lessons/52850042/concepts/528621220923

## Texture atlas

https://www.codeandweb.com/texturepacker
https://en.wikipedia.org/wiki/Texture_atlas
https://classroom.udacity.com/courses/cs255/lessons/49464373/concepts/731629460923#

## Pronađi uska grla

Focus on small portions of code that take lots of resources. It makes no sense to spend time working on a linear piece of code. Evil hides in loops, especially when lots of iterations and complex processing goes on inside. Recursion is also a great hiding place for slow code.

## Precompute Everything

Study your code carefully and detect values that are computed in complex arithmetic functions. Does your code use trigonometric functions, random numbers, or any other kind of complex mathematical routine? Try to tabulate those so the only processing that takes place inside the loop is the table lookup.

The following example is going to consume more CPU cycles than you might expect:
```c++
float acc = 0;
for (i = 0; i<1000; i++)
   acc = acc + i * sin(x * i);
```

Substituting the sin call with a table lookup (and precomputing the sine function into that table) produces a five times speed increase on a regular PC.

## Simplify Your Math

On a regular PC, a divide costs one and a half times a multiply, so it is a good idea to check for performance on your target platform. The following two snippets perform the same task, but the second version only has 60 percent of the timing cost of the divide version:

```c++
float acc = 1000;
for (long i = 0; i<100; i++)
   acc = acc / 2.0;

float acc = 1000;
for (long i = 0; i<100; i++)
   acc = acc*0.5;
```

Some operations that should be avoided at all costs are square roots, logarithmic operators, and so on. Try to simplify equations and, if you really need to use complex math routines, tabulate them before.

Square roots are expensive to calculate on most computers, so game programmers should always compared squared magnitudes whenever it is valid to do so. Na primer:
```
d^2 > (r1 + r2)^2
```
