# Pitagorina teorema

Pitagorina teorema glasi:
```
a^2 + b^2 = c^2
```
gde su `a` i `b` kraće stranice trougla a `c` je hipotenuza.

![pitagorina-teorema-primena](slike/pitagorina-teorema-primena.jpg?row=true)

Pitagorina teorema važi samo za pravougle trouglove.

# Primena

## Rastojanje između dve tačke

Often in programming, you want to know the distance between two points on the screen.

![rastojanje](slike/rastojanje.png?row=true)

The easiest way to do that is to use the Pythagorean theorem.

![rastojanje-izmedju-tacaka](slike/distance.png?row=true)

```js
a = x1 - x2
b = y1 - y2
c = Math.sqrt(a*a + b*b);
```

Pravolinijska razdaljina između dve tačke se naziva Euklidskom razdaljinom. 3D primer uključuje i `z` osu:

```js
distance = Math.sqrt( Math.pow(x2 − x1, 2) + Math.pow(y2 − y1, 2) + Math.pow(z2 − z1, 2) )
```
