# Matrice

Matrica je niz brojeva, poređanih u redove i kolone (tabela brojeva). Tako, matrica `2 x 3` ima 2 reda i 3 kolone. Ako matrica ima isti broj vrsta i kolona, onda je kvadratna matrica.

Matrica `-A` je suprotna matrica matrici `A`.

## Rotacija matrice?

Matrice su kao 2-dimenzionalni vektori. Na primer, tipična 2x2 matrica može izgledati ovako:

```
a c
b d
```

Kada množimo matricu vektorom, sabiramo proizvod (*dot product*) svakog reda matrice sa vektorom. Na primer, ako pomnožimo gornju matricu sa vektorom `(x, y)`, dobijamo:

```
(a, c) • (x, y) + (b, d) • (x, y)
```

Ili napisano na drugi način:

```
x(a, b) + y(c, d)
```

Ovo je potpuno isti izraz koji koristimo kada menjamo bazne vektore! Dakle, množenje `2x2` matrice sa 2D vektorom je isto što i menjanje njenih baznih vektora. Na primer, ako stavimo standardne bazne vektore (1,0) i (0,1) u kolone matrice, dobijamo:

```
1 0
0 1
```

Ovo je matrica identiteta, koja nema efekta. Ako dodamo osnove rotacije od 49 stepeni, dobijamo:

```
0.66 -0.75
0.75  0.66
```

Ova matrica će rotirati bilo koji 2D vektor u smeru suprotnom od kazaljke na satu za 49 stepeni.

## Operacije nad matricama

Matrice se mogu sabirati, množiti, transponovati i invertovati. 

Matrične operacije se često koriste u razvoju igara. Na primer, množenje matrica može se koristiti za izračunavanje kretanja objekata, a transponiranje za izračunavanje rotacija ili transformacija objekata.

### Sabiranje i oduzimanje matrica

![matrix_operations](slike/matrix_operations.jpg)

Matrice istih dimenzija se mogu sabirati, tako što saberemo pripadajuće elemente (odnosno brojčane vrednosti u istom položaju u obje matrice). 

Na primer, ako imamo matrice A i B, za svaki element računamo zbir[i][j] = A[i][j] + B[i][j]. 

U kodu:

```c
Matrix3X3 addMatrices(Matrix3X3 a, Matrix3X3 b)
{
  Matrix3X3 newMatrix;
  for(int i = 0; i<3; i++){
    for(int j=0; j<3; j++){
      newMatrix[i][j] = (a[i][j] + b[i][j]);
    }
  }
  return newMatrix;
}
```

Oduzimanje matrica radi na isti način, samo oduzimamo pripadajuće elemente.

### Množenje matrice skalarom

Matrica se množi nekim brojem tako što se svi elementi matrice pomnože tim brojem.

### Množenje matrica

Množenje dve matrica je moguće samo ako je broj kolona prve jednak broju redova druge. Za matrice ne važi komutativnost množenja: `A x B != B x A`.

Matrice A i B množimo tako što pomnožimo kolone matrice A sa redovima matrice B (tj. redom računamo proizvod (*dot product*) vektora kolone i vektora reda). 

![mnozenje-matrica](slike/mnozenje-matrica.png)

Na primer, ovako bismo pomnožili dve 3x3 matrice:

```cpp
Matrix3X3 multiply3X3Matrices(Matrix3X3 a, Matrix3X3 b) {
  Matrix3X3 newMatrix;
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      for (int k = 0; k < 3; k++) {
        newMatrix[i][j] += (a[i][k] * b[k][j]);
      }
    }
  }
  return newMatrix;
}
```

Procedura je drugačija kada množimo dve matrice različitih veličina:

```cpp
Matrix3X1 multiplyMatrixNxM(Matrix3X3 a, Matrix3X1 b) {
  Matrix3X1 newMatrix;
  newMatrix[0] = 0;
  newMatrix[1] = 0;
  newMatrix[2] = 0;
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      newMatrix[i] += (a[i][j] * b[j]);
    }
  }
  return newMatrix;
}
```

Imajte na umu dva važna aspekta množenja matrica:
* dva vektora moraju imati isti broj elemenata da bi dobili proizvod.
* proizvod (*dot product*) je skalarna vrednost (običan broj).

### Transponovanje matrica

Transponovanje je zamena redova i kolona matrice. To znači da će elementi koji su bili u istom redu biti u istoj koloni, a elementi koji su bili u istoj koloni biti u istom redu. Na primer, ako imamo matricu od 2 reda i 3 kolone, njena transponovana matrica će imati 3 reda i 2 kolone.

Transponovana matrica A se označava kao AT. To znači da redovi A postaju kolone AT, a kolone A redovi AT.

![matrix-transpose](slike/matrix-transpose.gif)

Primer:

```cpp
Matrix4X4 transpose4X4Matrix(Matrix4X4 a) {
  Matrix4X4 newMatrix;
  for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 4; j++) {
      newMatrix[i][j] = a[j][i];
    }
  }
  return newMatrix;
}
```

### Invertovanje

Invertovanje matrice je matematička operacija koja se primjenjuje na kvadratne matrice kako bi se dobila inverzna matrica, koja se potom množi s prvotnom matricom da bi se dobila jedinična matrica.

Jedinična matrica je matrica koja ima jedinice na glavnoj dijagonali (od gornjeg levog do donjeg desnog ugla) i nule na svim drugim pozicijama. Na primjer, 2x2 jedinična matrica izgleda ovako:

```
1 0
0 1
```

Ne mogu se sve matrice invertirati. Matrice koje se ne mogu invertirati zovu se singularne matrice.

Postupak za invertovanje matrice može biti složen, posebno za velike matrice, ali postoje programi koji ga mogu automatizirati.