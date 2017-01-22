# Pitagorina teorema

Pitagorina teorema glasi:
```
a^2 + b^2 = c^2
```
gde su `a` i `b` kraće stranice trougla a `c` je hipotenuza.

![pitagorina-teorema-primena](slike/pitagorina-teorema-primena.jpg)

Pitagorina teorema važi samo za pravougle trouglove.

# Primena

## Rastojanje između dve tačke

Često u programiranju želite da znate rastojanje između dve tačke na ekranu.

![rastojanje](slike/rastojanje.png)

Najlakši način da to izračunate je Pitagorina teorema.

![rastojanje-izmedju-tacaka](slike/distance.png)

Primer u kodu:
```js
a = x1 - x2
b = y1 - y2
c = Math.sqrt(a*a + b*b);
```

Pravolinijska razdaljina između dve tačke se naziva Euklidskom razdaljinom. 3D primer uključuje i `z` osu:

```js
distance = Math.sqrt( Math.pow(x2 − x1, 2) + Math.pow(y2 − y1, 2) + Math.pow(z2 − z1, 2) )
```
