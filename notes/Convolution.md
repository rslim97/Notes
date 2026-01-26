
$W_{out} = \frac{W_{in}+2P+K}{stride}+1$, assuming same padding p left & right i.e. p_left=p_right.

Note: If we pad original img with K//2 left & right, 
padded original image size = 10 + 3//2 + 3//2 = 12
convolve with kernel of size K = 3
$W_{out} = \frac{12+0-3}{1}+1 = 9+1 = 10$

Note: This property is used in conv backprop,
$W_{in} = 10$
$kernel\_size = 3$
$W_{out}=\frac{10+0-3}{1}+1=8$

pad output with K-1 left & right,
$W_{out\_padded} = 8+2+2 = 12$
convolve output with kernel size of K:
$\frac{12+0-3}{1}+1=10$. Since $dLdx = dLdz\circledast flipped(W)$, where $W$ is the filter.
