1. Convolution formula $W_{out} = \frac{W_{in}+2P+K}{stride}+1$.
2. Tip: By padding the input image with $K//2$ the output will be of the same width and height with the input. example:
	1. padded image size = 10 + 3//2 + 3//2 = 12
	2. convolve with kernel of size K = 3.
	3. get original size back: $W_{out} = \frac{12+0-3}{1}+1 = 9+1 = 10$
3. Tip: By padding the output with $K-1$, and convolving it with the kernel will return an feature map with the same size as the original input. This property is used in conv backprop, example: 
	1. Original input size: $W_{in} = 10$
	2. $kernel\_size = 3$
	3. $W_{out}=\frac{10+0-3}{1}+1=8$
	4. now pad output with $K-1$,
	5. $W_{out\_padded} = 8+2+2 = 12$
	6. convolve resulting output with kernel size of $K$:
	7. $\frac{12+0-3}{1}+1=10$. 
	8. Since in backpropagation, $dLdx = dLdz\circledast flipped(W)$, where $W$ is the filter.
4. How big is our receptive field?
	1. $r_0=\sum_{l=1}^{L}\left((k_l-1)\prod_{i=1}^{l-1}s_i\right)+1$
		1. $r_0$ is receptive field size
		2. $k_l$ is kernel size at layer $l$.
		3. $\sum_{l=1}^{L}$ sum over network layers.
		4. $\prod_{i=1}^{l-1}$ is the product of strides up to layer $l$.
