## Matrice

Matrica je pravougaoni niz brojeva, poređanih u redove i kolone.

Matrices can be added, multiplied, transposed, and inverted.

Matrix operations can be used to move 2D objects around on the screen and manipulate 3D objects within the world coordinate system.

You can create a class that would allow the programmer to create matrices of any size.

### Sabiranje i oduzimanje matrica

![matrix_operations](slike/matrix_operations.jpg?row=true)

Always make sure that both matrices are the same size before you attempt to add them. If A and B are both 3x3, so you can add them together.

Here is a sample function that shows how to add matrices in code:

```c
Matrix3X3 addMatrices(Matrix3X3 a, Matrix3X3 b)
{
  Matrix3X3 temp;
  for(int i = 0; i<3; i++){
    for(int j=0; j<3; j++){
      temp.index[i][j] = (a.index[i][j] + b.index[i][j]);
    }
  }
  return temp;
}
```

Subtracting matrices works exactly the same way; you just subtract corresponding entries.

### Množenje matrica

You can multiply matrices by taking a series of dot products. Keep in mind two important aspects of the dot product:
* The two vectors must have the same number of entries to take the dot product.
* The dot product returns a scalar quantity (a single number).

![mnozenje-matrica](slike/mnozenje-matrica.png?row=true)

Here is a function that allows us to multiply two 3x3 matrices:
```cpp
Matrix3X3 multiply3X3Matrices(Matrix3X3 a, Matrix3X3 b) {
  Matrix3X3 temp = createFixed3X3Matrix(0);
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      for (int k = 0; k < 3; k++) {
        temp.index[i][j] += (a.index[i][k] * b.index[k][j]);
      }
    }
  }
  return temp;
}
```

This process is only slightly different when multiplying two different sized matrices:
```cpp
Matrix3X1 multiplyMatrixNxM(Matrix3X3 a, Matrix3X1 b) {
  Matrix3X1 temp;
  temp.index[0] = 0.0 f;
  temp.index[1] = 0.0 f;
  temp.index[2] = 0.0 f;
  for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
      temp.index[i] += (a.index[i][j] * b.index[j]);
    }
  }
  return temp;
}
```

### Transponovana matrica

The transpose operation simply swaps each entry's row and column.

![matrix-transpose](slike/matrix-transpose.gif?row=true)

How to transpose a 4x4 matrix in code:
```cpp
Matrix4X4 transpose4X4Matrix(Matrix4X4 a) {
  Matrix4X4 temp;
  for (int i = 0; i < 4; i++) {
    for (int j = 0; j < 4; j++) {
      temp.index[i][j] = a.index[j][i];
    }
  }
  return temp;
}
```

http://alfonse.bitbucket.org/oldtut/Positioning/Tut04%20The%20Matrix%20Has%20You.html
