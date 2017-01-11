# Kretanje

In a game, you can set an object’s position to whatever you want. However, in the real world, you can never actually set the position of anything. Instead, the object has a position, which is modified by a motion vector (the combination of speed and direction). You have to apply force vectors to indirectly change the motion, which will change the position.

When you need to work with moving objects, you’ll be interested in their position, velocity, and acceleration. Velocity is the change in position over time, and likewise acceleration is the change in velocity over time. You calculate them like this:

```cpp
Vec3 CalcVelocity(Vec3 pos0, Vec3 pos1, float time)
{
  return (pos1 - pos0) / time;
}
```

```cpp
Vec3 CalcAcceleration(Vec3 vel0, Vec3 vel1, float time)
{
  return (vel1 - vel0) / time;
}
```

When an object moves through space, its location always references the center of mass.

## Njutnovi zakoni kretanja

Isaac Newton discovered three laws that govern all motion on Earth (except for on the molecular level) in the late 17th century.

* Svako telo ostaje u stanju relativnog mirovanja ili ravnomernog pravolinijskog kretanja sve dok ga dejstvo drugog tela ne prisili da to stanje promeni. (Neometano, ako se telo kreće, kretaće se, ako miruje, mirovaće). This specifies what happens when the net force is 0.

*	Ubrzanje je srazmerno dejstvujućoj sili, a obrnuto srazmerno masi tela. (Ubrzanje izaziva sila, a protivi mu se masa.)
```
a = F / m
```
odnosno:
```
F = m * a
```

The biggest difference between one-dimensional and two or three-dimensional motion involves the direction. To describe motion in two or three dimensions, we must incorporate vectors. The equations for 2D motion are:
```
ΣFx = m * ax
ΣFy = m * ay
```
U 3D kretanju se dodaje i z osa:
```
ΣFz = m * az
```

*	Sila kojom jedno telo deluje na drugo telo jednaka je po intenzitetu sili kojom drugo telo deluje na prvo, ali je suprotnog smera. (Na primer, kada top ispaljuje projektil, projektil ga pomera nazad.)

Force is typically measured in Newtons. One Newton is the force required to accelerate one kilogram at a rate of one meter per second squared:
`N = (kg)m / s^2`

## Kintetika (nauka o kretanju)

Kintetika je grana klasične mehanike koja se bavi kretanjem i njegovim uzrocima. In kinetics, the most important equation that you must consider is Newton’s second law.

When rigid bodies are involved, you must consider that the forces acting on the body will tend to cause rotation of the body.

Here is the general procedure for solving kinetics problems of interest to us:
1. Calculate the body’s mass properties (mass, center of mass, and moment of inertia).
2. Identify and quantify all forces and moments acting on the body.
3. Take the vector sum of all forces and moments.
4. Solve the equations of motion for linear and angular accelerations.
5. Integrate with respect to time to find linear and angular velocity.
6. Integrate again with respect to time to find linear and angular displacement.

Kinetic energy is a form of energy associated with moving bodies. It is equal to the energy required to accelerate the body from rest, which is also equal to the energy required to bring the moving body to a stop.

## Kinematika

Kinematika je grana klasične mehanike koja proučava kretanje, ne uzimajući u obzir njihovu masu ni sile koje uzrokuju kretanje.

## Equations of Motion (jednačine kretanja)

Equations of motion hold only when the acceleration is constant. If you have a scenario in which the acceleration changes, just break it into smaller time intervals of constant acceleration. This works perfectly in programming, because you address motion on a frame-by-frame basis.

These five equations can help you solve any problem related to one-dimensional motion with constant acceleration:

* final velocity = initial velocity + acceleration * time
* average velocity = (initial velocity + final velocity) / 2
* displacement = 1/2 (initial velocity + final velocity) * time
* displacement = initial velocity * time + 1/2 acceleration * time^2
* final velocity^2 = initial velocity^2 + 2 * acceleration * displacement.

In a 3D world, we’re going to use the same formulas, but the inputs are going to be 3D vectors to represent position, speed, and acceleration. Luckily, these vectors work exactly the same as scalars in these equations.

## Razdaljina (distance) i pomeraj (displacement)

Displacement is the vector version of distance.

When calculating displacement, all you care about is where the object starts and where it ends. Whatever happens in between doesn't matter. Football is a good example of displacement versus distance. Suppose player catches the ball on the 20-yard line and starts running. There's a blocker in the way, so the receiver circles around the blocker, avoids the other defender running toward him, and eventually gets tackled on the 50-yard line. The positive 30 yards is his displacement even though the actual distance traveled is much more.

![distance-vs-displacement](slike/distance-vs-displacement.png?row=true)

## Brzina (speed) i usmerena brzina (velocity)

Velocity is the vector version of speed. For example, 50km/h is just a scalar (speed). However, 50km/h due east is a vector (velocity).

Usmerena brzina (velocity) je vektorska verzija brzine. Usmerena brzina se izvodi iz pomeraja (displacement) u odnosu na vreme:
`v = Δs/Δt`
where Δs is distance traveled over the time interval Δt.

Prosečna brzina u kodu:
```java
float calcAvgVel(float start, float end, float time)
{
  return (end - start)/ time;
}
```

If you care only how fast an object is moving, use the speed. If you're trying to guide the motion of an object on the screen, always use velocity.

## Acceleration (ubrzanje)

Any time an object's velocity changes, it experiences an acceleration; it speeds up or slows down. The faster an object speeds up, the higher the acceleration. If the velocity doesn't change at all, the acceleration must be 0.

Average acceleration is change in velocity over change in time:
`a = Δv/Δt`

This function will calculate the acceleration in seconds:
```java
float calcAccelerationSeconds( float startVel, float finalVel, float time)
{
  return (finalVel - startVel) / time;
}
```

Any time you step on the gas pedal, the car speeds up or accelerates. As soon as you release the gas pedal, the car starts to slow down or decelerate. The only way to avoid accelerating is to turn on the cruise control.

Ako čovek padne sa bicikla... If the same biker crashes while riding downhill, the slightly faster speed does quite a bit more damage because acceleration has a time squared component and is therefore much more serious than a change in mass.

## Momentum

Momentum is defined as mass times velocity.
```
p = m * v
```

Because momentum is based on velocity, which constantly changes, it makes sense to talk about instantaneous momentum at specific points in time or change in momentum over a time interval.

Trik: Add a small force vector every frame in the direction the vehicle is currently facing, to simulate momentum. It’s important that this force vector be a percentage of the speed rather than a literal value.

## Inercija

When we wish to change the speed, the body shows a certain resistance against such changes. This resistance, called inertia, is a result of the body's mass. The larger the mass of the body, the smaller the change of speed will be.
