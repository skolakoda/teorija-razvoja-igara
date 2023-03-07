# 3D matrice

3D matrice funkcionišu isto kao 2D, samo imaju tri kolone za osnovne vektore umesto dve. Ako su osnovni vektori (a, b, c), (d, e, f) i (g, h, i), matrica bi bila:

```
a d g
b e h
c f i
```

## Matrica translacije

$$
T = \begin{bmatrix}
 1& 0&  0& 0\\ 
 0&  1& 0& 0\\ 
 0&  0&  1& 0\\ 
 t_{x}& t_{y}&  t_{z}& 1\\
\end{bmatrix}
$$

## Matrica skaliranja

$$
S = \begin{bmatrix}
 S_{x}&  0&  0& 0\\ 
 0&  S_{y}&  0& 0\\ 
 0& 0&  S_{z}& 0\\ 
 0&  0&  0& 1
\end{bmatrix}
$$

## Matrice rotacije

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
