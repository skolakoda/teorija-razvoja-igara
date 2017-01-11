## Energija

Energy is an alternative approach to modeling motion (pored sile).

### Rad

In physics, work has a very precise definition. Rad je prenos energije iz jednog sistema u drugi, koji se vrši delovanjem sile duž nekog puta. Rad je jednak proizvodu sile i pređenog puta (displacement), ako sila deluje u pravcu pomeranja tela.

```
W = F * Dx
```

Object must move for work to be done.

The force is measured in Newtons, and the displacement is measured in meters, which means that the work is measured in Newton-meters (N*m). This unit has been renamed the joule (J), so `1 J = 1 N * m`.

Programming the calculation for work is fairly straightforward. Here is a function that returns the amount of work done (in Joules), given a force, a friction force, and a displacement:

```java
float calculateWork(float force, float friction, float displacement)
{
  float netForce = force - friction;
  float temp = displacement * netForce;
  return temp;
}
```

Here is a function that will return the amount of work done considering an angled force:

```java
float calculateAngledWork(vector2D vect, float friction,float displacement)
{
  float temp;
  //don't forget to convert to rads....
  temp = cos(DegreesToRads(vect.y));
  float horizForce = vect.x * temp;
  float work = calculateWork(horizForce, friction, displacement);
  return work;
}
```

### Kinetic Energy

Kinetic energy is the amount of energy an object has because it is moving. Therefore, the faster it's moving, the more kinetic energy it has. It's similar to momentum, which is mass times velocity.

The kinetic energy is one-half of the mass times the speed squared:
```
KE = 1/2m * v^2
```

Notice that the definition is based on speed rather than velocity. Because kinetic energy is also a scalar quantity, the direction doesn't matter.

This function will calculate kinetic energy given a mass in kilograms and a speed in meters per second:

```java
float calculateKineticEnergy(float mass, float speed)
{
  float KE;
  KE = (mass/2) * (pow(speed,2));
  return KE;
}
```

Work-Energy Theorem states that the total work done on an object is equal to the change in its kinetic energy.
```
W = DKE = KE f – KE i
```

### Potential Energy

Gravitational potential energy (GPE) is the energy stored in an object due to its height off the ground. If you picked up this book and held it in the air, it would have gravitational potential energy. The potential energy was stored in the book until it was released.
```
GPE = m * g * y
```
(m = mass, g = acceleration due to gravity, y = height)

There are other types of potential energy, such as elastic potential energy.

### Zakon očuvanja energije (Conservation Law)

After being towed up the first hill, you do not need any additional motors until you reached the very end. The entire ride was governed by the law of conservation of energy. This law says that energy cannot be created or destroyed. It can only switch forms.

```
KE i + PE i = KE f + PE f
```

The faster an object moves, the more kinetic energy it has, and the higher it is off the ground, the more potential energy it has. What's fascinating is that the total amount of energy always remains the same.

As time goes on, energy is lost. In real life, some energy is lost to heat and sound because of friction and air resistance, but calculating the precise amount can be quite expensive in terms of processing power.

Cheat: adding an extra value that represents heat and sound energy to the left side of the conservation law forces a reduction in kinetic and potential energy, which produces a more realistic result.
