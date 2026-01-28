### 1D ###
1. Projective geometry on a line, $\mathrm{P}^2$.
2. In a 1D world, a point in homogeneous coordinates can be represented as $x'=\begin{pmatrix}x_1 \\ x_2\end{pmatrix}$, 1 __degrees of freedom__.
3. if $x_2=0$, the point will be a point at infinity, or an ideal point.
4. A projective transformation of a line is represented by $H_{2\times 2}$, i.e.
	1. $x'=H_{2\times 2}x$
	2. $H_{2\times 2}$ has __three degrees of freedom__, corresponding to four elements less one for scaling and can be computed from three points.
5. Cross ratio:
	1. $Cross(x_1,x_2,x_3,x_4)=\frac{\lvert{x_1x_2}\rvert\lvert{x_3x_4}\rvert}{\lvert{x_1x_3}\rvert\lvert{x_2x_4}\rvert}$, where $x_ix_j=\det{\begin{bmatrix}x_{i1}&&x_{j1}\\x_{i2}&&x_{j2}\end{bmatrix}}$
	2. $x'=H_{2\times 2}x$ the cross ratio must be preserved, i.e. should be the same number.
	3. $Cross(x_1',x_2',x_3',x_4')=cross(x_1,x_2,x_3,x_4)$.
	4. Proof: substitute $x'=H_{2\times 2}x$, into the formula $Cross(x_1',x_2',x_3',x_4')$.
### 2D ###
1. Homogenize a point in 2D $\begin{pmatrix}x\\ y\end{pmatrix}$ by adding a new dimension, $\begin{pmatrix}x \\ y \\ 1\end{pmatrix}$ and replacing $x$ with $\frac{x_1}{x_3}$ and $y$ with $\frac{x_2}{x_3}$. Or equivalently add a new dimension and now can multiply all dimension by a scale $k$, $\begin{pmatrix}kx\\ ky \\ k\end{pmatrix}=\begin{pmatrix}x'\\ y'\\ w'\end{pmatrix}$
2. From the equation of a line in 2D, 
3. $\begin{align*}ax+by+c&=0 \\a(kx)+b(ky)+c(k)&=0\\ax_1+bx_2+cx_3&=0 \\l_1x_1+l_2x_2+l_3x_3&=0\end{align*}$
4. In $\mathrm{P}^2$ both a line $\begin{pmatrix}l_1 \\ l_2 \\ l_3 \end{pmatrix}$ and a point $\begin{pmatrix}x_1 \\ x_2 \\ x_3 \end{pmatrix}$ has __two degrees of freedom__. 
5. Intersection of a point and a line or a line and a point in homogeneous coordinates, $$l^{T}x=0$$
6. line formed by two points 
	1. algebraic derivation
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

	2.  line formed by two points is the normal vector of the plane formed by the two lines, by taking the cross product (geometric interpretation).
7. point intersected by two lines 
	1. algebraic derivation, 
$$
\begin{align*}
l_1x_1+l_2x_2+l_3x_3 &= 0 \\
l_1'x_1+l_2'x_2+l_3'x_3 &= 0 \\
\end{align*}$$
		1. Symmetrical to the derivation of line formed by two points case.
		2. $x=l \times l'$
	2. point intersected by two lines is the direction vector of a line formed by the intersection of two planes (geometric interpretation).
8. Conics
	-  
	$$\begin{align*}
	ax^2 + bxy + cy^2 + dx + ey + f &= 0 \\ 
	ax_1^2 + bx_1x_2 + cx_2^2 + dx_1 + ex_2 + f &= 0 \\
	\end{align*}
	$$
	- Representation of a conic, 5 dof $$\begin{pmatrix}a\\b\\c\\d\\e\\f\end{pmatrix}$$
	- To represent the relationship between conic and points, we write $$x^TCx = 0$$
	- $C = \begin{bmatrix}a && b/2 && d/2\\ b/2 &&c && e/2 \\ d/2 && e/2 && f\end{bmatrix}$
	- The intrinsic camera parameters matrix is an example of a conic (has 5 dof).
	- C is a homogeneous representation of a conic.
	- Only ratios of the matrix elements are important, multiplying $C$ by a non-zero scalar has no effect.
	- The conic has __five degrees of freedom__ which can be thought of the ratios ${a:b:c:d:e:f}$.
	- Each point $x_i=(x_i,y_i)$ places one constraint on the conic coefficients:
		$$ ax_i^2+bx_iy_i + cy_i^2 + dx_i + ey_i + f = 0 $$
	- Where $$ c = \begin{pmatrix}a,b,c,d,e,f\end{pmatrix}^T $$ is the conic $C$ represented by a 6-vector.
	$$\begin{bmatrix}x_1^2 && x_1y_1 && y_1^2 && x_1 && y_1 && 1 \\
	&& && \ldots && && \\
	&& && \ldots && && \\
	&& && \ldots && && \\
	&& && \ldots && && \\
	\end{bmatrix}\begin{pmatrix}a\\b\\c\\d\\e\\f\end{pmatrix} = 0$$
	- The $A_{5\times 6}$. The conic is a null vector of this $5\times 6$ matrix. Can be solved using SVD, and taking the eigenvector of $V$ corresponding to the smallest eigenvalue, i.e. the one with the least principal component. 
	- This shows that a conic is determined uniquely (up to scale) by five points in general.
	
	```
	|          | Dual       |
	| -------- | -------    |
	|point     | line       |
	|conic     | dual conic |
	```
9. Tangent line to conics:
	1. Intersection of point $x$ and tangent line: $l^Tx=0$
	2. Intersection of point and conic: $x^TCx = 0$
	3. get $l^Tx=x^T(Cx)=0$, recall $x^Tl=l^Tx$.
	4. Therefore $l=Cx$.
10. Dual conic, based on the definition of a point conic, $x^TCx=0$, a line conic would have the form: $l^TC^*l=0$. Where $l$ is a tangent to the conic $C$.
11. 
```
	| Conic      | Dual Conic|
	| --------   | ------- |
	| $x^TCx=0$  | $l^TC^*l=0$    |
```
14. A dual conic has __five degrees of freedom__, and can be computed from five lines.
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
$$
	- Recall $$(A^T)^{-1}=(A^{-1})^T$$ if $A$ is an $n\times n$ invertible matrix. Since $C$ is symmetric $C^{-1}=C^{-T}$.
16. Degenerate conic
	1. first degenerate conic: A degenerate conic made of 2 straight lines.
		1. $C=lm^T + ml^T$
		2. $l$ and $m$ are lines. Points on $l$ satisfy $l^Tx=0$, similarly $m^Tx=0$. The two lines themselves is the conic.
		3. Proof: $x^TCx = x^T(lm^T+ml^T)x = (x^Tl)(m^Tx)+(x^Tm)(l^Tx)=0$
		4. which consists of $x^Tl=l^Tx=l_1x_1+l_2x_2+l_3$.
		5. and $m^Tx = x^Tm = m_1x_1 + m_2x_2 + m_3x_3$.
		6. has rank(C) = 2.
	2. Second degenerate conic: made of one line or two duplicate lines.
		1. $C=ll^T + ll^T$
		2. Similarly we have $l^Tx=0, x^Tx=0$
		3. $x^TCx = x^T(ll^T+ll^T)x = (x^Tl)(l^Tx) + (x^Tl)(l^Tx) = 0$
		4. which consists of $x^Tl=l^Tx=l_1x_1+l_2x_2+l_3$
		5. has rank(C) = 1.
	3. Third degenerate conic: made of two points.
		1. $C^* = xy^T + yx^T$ has rank(C) = 2.
	4. Fourth degenerate conic:  made of a point or two duplicate points.
		1. $C^* = xx^T + xx^T$ has rank(C)=1.
```
	| Degenerate Conic      | Degenerate Dual Conic|
	| --------------------- | -------------------- |
	| $ml^T + lm^T$         | $xy^T + yx^T$        |
	| $ll^T + ll^T$         | $xx^T + xx^T$        |
```
17. Planar projective transformations for points
	1. Projectivity, mapping from $\mathrm{P}^2$ to $\mathrm{P}^2$.
	2. such that three points $x_1$, $x_2$, and $x_3$. Why three? (because a plane in 3D has three degrees of freedom?) lie on the same line if and only if $h(x_1)$, $h(x_2)$, $h(x_3)$ do.
	3. $x' = hx \Rightarrow x=h^{-1}x'$.
	4. Define planar projective transformation, a transformation matrix for objects in 2D plane for example points or lines (in homogeneous coordinates, knowing points or lines have two degrees of freedom, and bumping the dimension by one, i.e. from 2 to 3 coordinates, and keeping the same number of dof), we have:
	5. $$\begin{pmatrix}x_1'\\x_2'\\x_3'\end{pmatrix}=\begin{bmatrix}
	h_{11}&&h_{12}&&h_{13} \\ h_{21}&&h_{22}&&h_{23} \\ h_{31}&&h_{32}&&h_{33}
	\end{bmatrix}\begin{pmatrix}x_1\\x_2\\x_3\end{pmatrix}$$
	6. or $x'=Hx$. $H$ is a $3\times 3$ matrix, and is homogeneous (only the ratio of the matrix elements is significant).
	7. $H$ has __eight degrees of freedom__, nine minus one for scaling.
18. Projective transformation of a line
	1. $l^Tx = 0$, $l'^Tx'=0$
	2. $l^T(H^{-1}H)x = 0$
	3. $(H^{-T}l)^Tx' = 0 \Rightarrow l' = H^{-T}l$
	4. Under a projective transformation $H$, the points that lie on a line $l$, will be transformed to points that lie on the line $l'=H^{-T}l$
	5. This means under the point transformation $x'=Hx$, a line transforms as $l'=H^{-T}l$ or $l'^T = l^TH^{-1}$.
19. Projective transformation of a conic
	1. projective transformation of a point, $x'=Hx \Rightarrow x=H^{-1}x'$
	2. $x^{T}Cx=(H^{-1}x')^TC(H^{-1}x')=x'^T(H^{-T}CH^{-1})x'$
	3. under a point transformation $x'=Hx$, a conic transforms according to $C'=H^{-T}CH^{-1}$
20. Projective transformation of a dual conic
	1. $l'=H^{-T}l \Rightarrow l=H^Tl'$
	2. $l^TC^*l=(H^Tl')^TC^*(H^Tl')=l'^T(HC^*H^T)l'$
	3. a dual conic $C^*$ transforms to $C^{*'}=HC^{*}H^T$
21. Hierarchy of transformations:
	1. General transformation for objects in a 2D plane such as points and lines $H_{3\times 3}$, with *eight degrees of freedom*
	2. Isometries: transform that preserves Euclidean distance
		1. $x'=H_{E}x = \begin{bmatrix}R && t \\ 0^T && 1\end{bmatrix}x=\begin{bmatrix}\epsilon c\theta && -s\theta && t_x \\ \epsilon s\theta && c\theta && t_y \\ 0 && 0 && 1\end{bmatrix}$, where $\epsilon=\pm 1$.
		2. $\epsilon=+1$, orientation preserving.
		3. $\epsilon=-1$, orientation reversing.
		4. Invariants: length, angle, area.
		5. $H_E$ has __three degrees of freedom__.
	3. Isotropic scaling:
		1. $H_S$ has __four degrees of freedom__.
		2. can be computer from two point correspondences.
	4. Affinity transform:
		1. $H_A$ has __six degrees of freedom__.
		2. can be computed from three point correspondences
		3. Note: each point correspondence would give __two degrees of freedom__, hence why the three points will be sufficient to compute this __six degrees of freedom__ matrix.
		4. can always be decomposed as:
			1. $A=R(\theta)R(-\phi)DR(\phi)$
			2. This decomposition follows directly from singular value decomposition.
	5. Projective transformation: a non-singular linear transformation of homogeneous coordinates.
		1. $x'=H_Px=\begin{bmatrix}A && t \\ \vec{v}^T && u\end{bmatrix}x$ where vector $\vec{v}=(v_1,v_2)^T$ and $u$ can be 0. 
		2. Note: it is not always possible to make $\begin{bmatrix}v^T && u\end{bmatrix}$ to be $\begin{bmatrix}0&&0&&1\end{bmatrix}$. 
		3. $H_P$ has nine elements with only the ratio of its elements is significant, so the transformation has __eight degrees of freedom__.
		4. can be computed from four point correspondences, with no three collinear on either plane.
		5. It is not possible to distinguish between orientation preserving and orientation reversing projectivities in $\mathrm{P}^2$.
		6. Decomposition of a projective transformation:
			1. $H=H_SH_AH_P=\begin{bmatrix}sR && t \\ 0^T && 1\end{bmatrix}\begin{bmatrix}K && 0 \\ 0^T && 1\end{bmatrix}\begin{bmatrix}I && 0 \\ v^T && u\end{bmatrix}=\begin{bmatrix}A && t \\ v^T && u\end{bmatrix}$
			2. $A$ is a non-singular matrix given by: $A=sRK + tv^T$
				1. where $s$ is the scale
				2. $R$ is the rotation matrix
				3. $K$ is an upper triangular matrix
				4. $t$ is translation vector
				5. $v^T$ is a $2\times 1$ vector
			3. Decomposition is valid if $u\neq 0$, and is unique if $s$ is chosen positive.
### 3D ###
1. Many properties and entities of $\mathrm{P}^3$ are straigthforward generalizations of those of $\mathrm{P}^2$. Example: The homogeneous coordinates of a point in $\mathrm{P}^3$ Euclidean 3-space is augmented with an extra dimension in $\mathrm{P}^2$. 
	1. Note: two lines always intersect on $\mathrm{P}^2$, but not always on $\mathrm{P}^3$.
2. Points in $\mathrm{P}^3$
	1. A point in 3-space represented in homogeneous coordinates as 4-vector, i.e. 
	2. $x = (x_1, x_2, x_3, x_4)^T$ with $x_4\neq 0$
	3. represents the point $(x, y, z)^T$ of $\mathrm{R}^3$ with inhomogeneous coordinates
	4. $x=x_1/x_4$, $y=x_2/x_4$, $z=x_3/x_4$. Homogeneous points with $x_4=0$ represent points at infinity.
3. Projective transformation of points in $\mathrm{P}^3$:
	1. A projective transformation acting on $\mathrm{P}^3$ is a linear transformation on $x$ by a non-singular $4\times 4$ matrix: $x' = H_{4\times 4}x$.
	2. The matrix $H$ is homogeneous and has __fifteen degrees of freedom__, sixteen elements less on for scaling.
	3. As in $\mathrm{P}^2$ space, the mapping is a collineation (lines are mapped to lines, which preserves incidence relations such as intersection point of a line with a plane, and order of contact).
4. Planes in $\mathrm{P}^3$ 
	1. A plane in 3-space may be written as:
		1. $\Pi_1 x + \Pi_2 y + \Pi_3 z + \Pi_4 = 0$ 
		2. Homogeneizing by $x=x_1/x_4$, $y=x_2/x_4$, $z=x_3/x_4$.
		3. $\Pi_1 x_1 + \Pi_2 x_2 + \Pi_3 x_3 + \Pi_4x_4 = 0$
		4. $\Pi^Tx=0$
	2. Which expresses that the key point $x$ is on the plane $\Pi = \begin{pmatrix}\Pi_1, \Pi_2, \Pi_3, \Pi_4 \end{pmatrix}^T$.
	3. Only three independent ratios ${\Pi_1:\Pi_2:\Pi_3:\Pi_4}$ of the plane coefficients are significant, i.e. __three degrees of freedom__.
	4. The first 3 components of $\Pi$ correspond to the plane normal of Euclidean geometry, i.e. $n=(\Pi_1, \Pi_2, \Pi_3)^T$.
5. Points in $\mathrm{P}^3$
	1. Analogous to a line in $\mathrm{P}^2$, we can rewrite  $\Pi^Tx=0$.  
	2. $n\cdot x + d = 0$.
	3. where $x = \begin{pmatrix}x, y, z\end{pmatrix}^T$, $x_4=1$ and $d=\Pi_4$.
	4. In this form $\frac{d}{\lVert{\vec{n}}\rVert}$ is the distance of the plane from the origin.
		1. Proof: using analogy to the the line in $\mathrm{P}^2$.
		2. equation of line in $\mathrm{P}^2$ in *inhomogeneous* coordinates: $\begin{pmatrix}a\\ b\end{pmatrix}^T\begin{pmatrix}x\\ y\end{pmatrix} + c =0$. Where $\vec{n}=\begin{pmatrix}a\\ b\end{pmatrix}$ and any point on the line $\vec{v}=\begin{pmatrix}x\\ y\end{pmatrix}$.
		3. closest distance from line to the origin $d$ is the dot product of a point on the line $\vec{v}$ with the unit normal vector.
		4. $d=\frac{|\vec{v}\cdot \vec{n}|}{\lVert\vec{n}\rVert}=\frac{c}{\sqrt{a^2 + b^2}}$
		5. extending this case to the plane in $\mathrm{P}^3$ we have the distance from the plane to the origin as $\frac{d}{\lVert \vec{n}\rVert}$, where $d=\Pi_4$ and $\lVert\vec{n}\rVert=\sqrt{\Pi_1^2+\Pi_2^2+\Pi_3^2}$ .
	5. Again similarly, under point transformation $x'=Hx$, a plane transforms as $\Pi' = H^{-T}\Pi$.
6. Geometric relations between planes and points and lines:
	1. Plane defined uniquely by the *join of three points* (not collinear), or the *join of a line and point* (not incident), in general position.
	2. Two distinct planes intersect in a *unique line*.
	3. Three distinct planes intersect in a *unique point*.