CenterNet
1. Start with image $I\in\mathbb{R}^{W\times{H}\times3}$ 

2. Training  for keypoint classification:
	1. The network will produce a keypoint heatmap $\hat{Y}\in[0,1]^{\frac{W}{R}\times\frac{H}{R}\times{C}}$ 
		1. R is the output stride
		2. C is the no. of keypoint types, for example:
			1. C=17 in human pose estimation
			2. C=80 object categories in object detection (COCO)
		3. use R=4, default in literature. R is downsampling stride. Image is downsampled R times in resolution.
	2. To construct the target $Y\in[0,1]^{\frac{W}{R}\times\frac{H}{R}\times{C}}$, 
		1. Let the ground truth keypoint in image pixel coordinate be $p=(p_x,p_y)$. Then compute $\tilde{p}$  the lower resolution equivalent of $p$ as:
			1. For example image is of size 28x28x3 divided by 4x4 tiles to become 7x7 grid cell. Say p=(26,27), R=4, 
				1. $\tilde{p}=\frac{P}{R}=(\frac{26}{4},\frac{27}{4})=(6.5,6.75)$, $\lfloor{\frac{P}{R}}\rfloor=(6,6)$, 
				2. $\tilde{p}=\frac{P}{R}=(\frac{25}{4},\frac{24}{4})=(6.25,6.)$, $\lfloor{\frac{P}{R}}\rfloor=(6,6)$. 
		2. $(x,y)$ being the coordinate of $Y$.
		3. Imagine point $(\tilde{p}_x,\tilde{p}_y)$ in the center and 8 points $(x_i,y_i)$ surrounding it.
		4. Then for each class c, splat the $c$th dimension of $Y$ with:
		5. $Y_{xyc}=\exp{(-\frac{(x-\tilde{p}_x)^2+(y-\tilde{p}_y)^2}{2\sigma_p})}$.
		6. If two gaussians of the *same* class overlap, we take the element wise maximum.
		7. The training objective is pixel wise logistic regression with focal loss:
		8. $$L_k=\sum_{xyc}-\frac{1}{N}\begin{cases}(1-\hat{Y}_{xyc})^{\alpha}\log{(\hat{Y}_{xyc})}\quad\text{if $Y_{xyc}=1$}\\(\hat{Y}_{xyc})^{\alpha}\log{(1-\hat{Y}_{xyc})}(1-Y_{xyc})^{\beta}\quad\text{, otherwise}\end{cases}$$
3. Training for keypoint localisation:
	1. $$L_{off}=\text{localisation error in x coordinate + localisation error in y coordinate}$$
	2. $$L_{off}=\frac{1}{N}(\sum_{\tilde{p}_x}\lvert{\hat{O}_{\tilde{p}_x} - (\frac{p_x}{R} - \lfloor\frac{p_x}{R}\rfloor)}\rvert + \sum_{\tilde{p}_y}\lvert{\hat{O}_{\tilde{p}_y} - (\frac{p_y}{R} - \lfloor\frac{p_y}{R}\rfloor)}\rvert$$
4. Training to recover width and height:
	1. $k$th Keypoint: $p_k=(p_x,p_y)$ with bbox:$(x_1,y_1,x_2,y_2)$, $p_k=(\frac{x_1+x_2}{2},\frac{y_1+y_2}{2})$
	2. $\hat{S}_k:$ predicted bbox width &height, $(\hat{x}_2^{(k)}-\hat{x}_1^{(k)},\hat{y}_2^{(k)}-\hat{y}_1^{(k)})$
	3. $S_k$ : ground truth width & height, $(x_2-x_1,y_2-y_1)$
	4. Without normalizing the scale and directly use raw pixel coordinates.
	5. $$L_{size}=\frac{1}{N}\sum_{p_k}\lvert\hat{S}_{p_k}-S_k\rvert$$
5. Then the overall training loss:
	1. $$L=L_k+\lambda_{size}L_{size}+\lambda_{off}L_{off}$$
	2. we set $lambda_{size}=0.1$ and $\lambda_{off}=1$, means penalize object center offset more than fitting object width & height.
6. The final output size is $(\frac{W}{R},\frac{H}{R},C+4)$