# 3D transformacione matrice

## Translacija

$$
T = \begin{bmatrix}
 1& 0&  0& 0\\ 
 0&  1& 0& 0\\ 
 0&  0&  1& 0\\ 
 t_{x}& t_{y}&  t_{z}& 1\\
\end{bmatrix}
$$

## Skaliranje

$$
S = \begin{bmatrix}
 S_{x}&  0&  0& 0\\ 
 0&  S_{y}&  0& 0\\ 
 0& 0&  S_{z}& 0\\ 
 0&  0&  0& 1
\end{bmatrix}
$$

## Rotacija

Matrice za rotaciju po x, y i z osi:

$$
R_{x}(\theta) = \begin{bmatrix}
 1& 0&  0& 0\\ 
 0&  cos\theta & −sin\theta& 0\\ 
 0&  sin\theta &  cos\theta& 0\\ 
 0& 0&  0& 1\\
\end{bmatrix}
R_{y}(\theta) = \begin{bmatrix}
 cos\theta& 0&  sin\theta& 0\\ 
 0&  1& 0& 0\\ 
 −sin\theta&  0&  cos\theta& 0\\ 
 0& 0&  0& 1\\
\end{bmatrix}
R_{z}(\theta) =\begin{bmatrix}
 cos\theta &  −sin\theta &  0& 0\\ 
 sin\theta &  cos\theta &  0& 0\\ 
 0& 0&  1& 0\\ 
 0&  0&  0& 1
\end{bmatrix}
$$

## Primeri

Osnovne transformacije pomoću matrica u Three.js-u:

```js
const matrix = new THREE.Matrix4()

function translate(mesh, param) {
  matrix.set(
    1, 0, 0, param.x,
    0, 1, 0, param.y,
    0, 0, 1, param.z,
    0, 0, 0, 1
  )
  mesh.applyMatrix4(matrix)
  mesh.verticesNeedUpdate = true
}

function scale(mesh, param) {
  matrix.set(
    param.x, 0, 0, 0,
    0, param.y, 0, 0,
    0, 0, param.z, 0,
    0, 0, 0, 1
  )
  mesh.geometry.applyMatrix4(matrix)
  mesh.geometry.verticesNeedUpdate = true
}

function rotateY(mesh, param) {
  const cos = Math.cos(param.theta)
  const sin = Math.sin(param.theta)
  matrix.set(
    cos, 0, sin, 0,
    0, 1, 0, 0,
    -sin, 0, cos, 0,
    0, 0, 0, 1
  )
  mesh.geometry.applyMatrix4(matrix)
  mesh.geometry.verticesNeedUpdate = true
}
```
