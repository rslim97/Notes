1. Homogenize a point in 2D $\begin{pmatrix}x\\ y\end{pmatrix}$ by adding a new dimension, $\begin{pmatrix}x \\ y \\ 1\end{pmatrix}$ and replacing $x$ with $\frac{x_1}{x_3}$ and $y$ with $\frac{x_2}{x_3}$. Or equivalently add a new dimension and now can multiply all dimension by a scale $k$, $\begin{pmatrix}kx\\ ky \\ k\end{pmatrix}=\begin{pmatrix}x'\\ y'\\ w'\end{pmatrix}$
2. From the equation of a line in 2D, $$\begin{align*}
ax+by+c&=0 \\
a(kx)+b(ky)+c(k)&=0\\
ax_1+bx_2+cx_3&=0 \\
l_1x_1+l_2x_2+l_3x_3&=0
\end{align*}$$
3. Inter section of a point and a line or a line and a point in homogeneous coordinates, $$l^{T}x=0$$
4. a line formed by two points (algebraic derivation)
 $$\begin{align*}
 l_1x_1+l_2x_2+l_3x_3&=0 \\
 l_1x_1'+l_2x_2'+l_3x_3'&=0 \\
 \frac{l_1}{l_3}\frac{x_1}{x_3} + \frac{l_2}{l_3}\frac{x_2}{x_3} + 1 &= 0 \\
 \frac{l_1}{l_3}\frac{x_1'}{x_3'} + \frac{l_2}{l_3}\frac{x_2'}{x_3'} + 1 &=0 \\
 ua+vb &= -1 \\
 uc+vd &= -1 \\
 \begin{bmatrix}a & b \\ c & d\end{bmatrix}\begin{bmatrix}u \\ v\end{bmatrix} &= \begin{bmatrix}-1 \\ -1\end{bmatrix} \\
 \begin{bmatrix}u \\ v \end{bmatrix} &= \frac{\begin{bmatrix}d && -b \\ -c && a \end{bmatrix} \begin{bmatrix}-1 \\ -1\end{bmatrix}}{ad-bc} \\
 u &= \frac{l_1}{l_3} = \frac{x_2x_3' - x_2'x_3}{x_1x_2' - x_2x_1'}\\
 v &= \frac{l_2}{l_3} = \frac{x_1'x_3 - x_1x_3'}{x_1x_2' - x_2x_1'}\\ 
 l &= x \times x'
	\end{align*}$$

5.  a line formed by two points is the normal vector of the plane formed by the two lines, by taking the cross product (geometric interpretation).
6. a point intersected by two lines (algebraic derivation)
$$
\begin{align*}
l_1x_1+l_2x_2+l_3x_3 &= 0 \\
l_1'x_1+l_2'x_2+l_3'x_3 &= 0 \\


\end{align*}$$
	1. Symmetrical to the derivation of line formed by two points case.
	2. $x=l \times l'$
7. a point intersected by two lines is the direction vector of a line formed by the intersection of two planes (geometric interpretation).
8. Conics
	-  
	$$\begin{align*}
	ax^2 + bxy + cy^2 + dx + ey + f &= 0 \\ 
	ax_1^2 + bx_1x_2 + cx_2^2 + dx_1 + ex_2 + f &= 0 \\
	
	\end{align*}
	$$
	- Representation of a conic, 5 dof $$\begin{pmatrix}a\\b\\c\\d\\e\\f\end{pmatrix}$$
	- $$$$
	- The intrinsic camera parameters matrix is an example of a conic (has 5 dof).
	- C is a homogeneous representation of a conic.
	- Only ratios of the matrix elements are important, multiplying $C$ by a non-zero scalar has no effect.
	- The conic has five degrees of freedom which can be thought of the ratios ${a:b:c:d:e:f}$.
	- Each point $x_i=(x_i,y_i)$ places one constraint on the conic coefficients:
		$$ ax_i^2+bx_iy_i + cy_i^2 + dx_i + ey_i + f = 0 $$
	- Where $$ c = \begin{pmatrix}a,b,c,d,e,f\end{pmatrix}^T $$ is the conic $C$ represented by a 6-vector.
	- This shows that a conic is determined uniquely (up to scale) by five points in general.
	
	```
	|          | Dual       |
	| -------- | -------    |
	|point     | line       |
	|conic     | dual conic |
	```
7. Tangent line to conics:
	1. Intersection of point $x$ and tangent line: $l^Tx=0$
	2. Intersection of point and conic: $x^TCx = 0$
	3. get $l^Tx=x^T(Cx)=0$, recall $x^Tl=l^Tx$.
	4. Therefore $l=Cx$.
8. Dual conic, based on the definition of a point conic, $x^TCx=0$, a line conic would have the form: $l^TC^*l=0$. Where $l$ is a tangent to the conic $C$.
9. 
```
	| Conic      | Dual Conic|
	| --------   | ------- |
	| $x^TCx=0$  | $l^TC^*l=0$    |
```
14. A dual conic has five degrees of freedom, and can be computed from five lines.
15. $l^Tx=0$, 
$$
\begin{align*}
x^TCx&=0 \\
\text{since } l&=Cx, \text{this implies} \\
x&=C^{-1}l\\
(C^{-1}l)^TC(C^{-1}l)&=0 \\
l^TC^{-T}CC^{-1}l&=0 \\
l^TC^{-T}l&=0 \\
\end{align*}
$$. Recall $$(A^T)^{-1}=(A^{-1})^T$$ if $A$ is an $n\times n$ invertible matrix. Since $C$ is symmetric $C^{-1}=C^{-T}$.
