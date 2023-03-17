# Matrice

Matrica je niz brojeva, poređanih u redove i kolone (tabela brojeva). Tako, matrica `2x3` ima 2 reda i 3 kolone. Ako matrica ima isti broj vrsta i kolona, onda je kvadratna matrica.

Matrice su kao 2-dimenzionalni vektori. Na primer, tipična 2x2 matrica može izgledati ovako:

```
a c
b d
```

<!-- Matrica `-A` je suprotna matrica matrici `A`. -->

## Operacije nad matricama

Matrice se mogu sabirati, množiti, transponovati i invertovati. 

Matrične operacije se često koriste u razvoju igara. Na primer, množenje matrica može se koristiti za izračunavanje kretanja objekata, a transponiranje za izračunavanje rotacija ili transformacija objekata.

### Sabiranje i oduzimanje matrica

![matrix_operations](slike/sabiranje.jpg)

Matrice istih dimenzija se mogu sabirati, tako što saberemo pripadajuće vrednosti iz obe matrice. Na primer, ako imamo matrice A i B, za svaki element računamo zbir[i][j] = A[i][j] + B[i][j]. 

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

### Množenje matrica

![mnozenje-matrica](slike/mnozenje.jpg)

Množenje dve matrica je moguće samo ako je broj kolona prve jednak broju redova druge. Matrice A i B množimo tako što pomnožimo kolone A sa redovima B (tj. redom računamo proizvod vektora kolone i vektora reda). 

Za matrice ne važi komutativnost množenja: `A x B != B x A`.

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
* proizvod (*dot product*) je skalarna vrednost.

### Množenje matrice skalarom

Matrica se množi nekim brojem tako što se svi elementi matrice pomnože tim brojem.

### Transponovanje matrica

Transponovanje je zamena redova i kolona matrice. To znači da će elementi koji su bili u istom redu biti u istoj koloni, a elementi koji su bili u istoj koloni biti u istom redu. Na primer, ako imamo matricu od 2 reda i 3 kolone, njena transponovana matrica će imati 3 reda i 2 kolone.

Transponovana matrica A se označava kao AT.

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

Invertovanje matrice je operacija koja se primjenjuje na kvadratne matrice kako bi se dobila inverzna matrica, koja se množi s prvotnom matricom da bi se dobila jedinična matrica.

Jedinična matrica je matrica koja ima jedinice na glavnoj dijagonali (od gornjeg levog do donjeg desnog ugla) i nule na svim drugim pozicijama. Na primjer, 2x2 jedinična matrica izgleda ovako:

```
1 0
0 1
```

Ne mogu se sve matrice invertirati. Matrice koje se ne mogu invertirati zovu se singularne matrice.

Postupak za invertovanje matrice može biti složen, ali postoje programi koji ga automatizuju.
