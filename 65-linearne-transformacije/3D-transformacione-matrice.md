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
