$$$$
1. from [2]:
	1. Self-attention is a seq2seq operation: a sequence of vectors goes in, and a sequence of vectors comes out. Let's call the input vectors $\vec{x}_1, \vec{x}_2, \ldots, \vec{x}_t$ and the corresponding output vectors $\vec{y}_1, \vec{y}_2,\ldots, \vec{y}_t$. The vectors all have dimension $k$.
	2. To produce output vector $\vec{y}_i$, the self attention operation simply takes a __weighted average over all the input vectors__ $\vec{y}_i=\sum_jw_{ij}\vec{x}_j$.
	3. where $j$ indexes over the whole sequence and the weights sum to one over all $j$. The weight $w_{ij}$ is not a parameter, as in a normal neural net, but is is *derived* from a function over $\vec{x}_i$ and $\vec{x}_j$. 
	4. The simplest option for this function is the dot product:
		1. $w_{ij}'=\vec{x}_i^T\vec{x}_j$.
		2. Note: $\vec{x}_i$ is the input vector at the same position as the current output vector $\vec{y}_i$. For the next output vector, we get an entirely new series of dot products, and a different weighted sum.
	5. The dot product gives us a value anywhere between negative and positive infinity, so we apply a softmax to map the values to $\text{[0, 1]}$ and ensure that they sum to 1 over the whole sequence:
		1. $w_{ij}  = \frac{\exp{w_{ij}'}}{\sum_j\exp{w_{ij}'}}$.
	6. And that's the basic operation of self attention.

2. from [3]:
	1. Ignoring details like normalization, biases, etc, fully connected networks are fixed (in position to the features) weights:
		1. $f(x)=(Wx)$ where $W$ is learned in training, and fixed in inference.
	2. Self-attention layers are dynamic, changing the weight as it goes:
		1. $\text{attn}(x) = (Wx)$
		2. f(x) = (attn(x) * x)
3. How attention works:
		1. We have a query vector $\vec{q}$ (e.g. the decoder state)
		2. We have input vectors $H=\begin{bmatrix}\vec{h}_1,\ldots,\vec{h}_L\end{bmatrix}^T$ (e.g. one per source word, encoder state)
		3. We compute affinity scores $s_1, \ldots s_L$ by "comparing" $q$ and $H$.  (here)
		4. We convert these scores to probabilities:
			1. $\vec{p}=\text{softmax}(\vec{s})$
		5. We use this to output a representation as a weighted average:
			1. $c=H^Tp=\sum_{i=1}^{L}p_i\vec{h}_i$  (here)
	1. Affinity scores
	2. Several ways of "comparing" a quey $\vec{q}$ and an input "key" vector $\vec{h}_i$:
		1. Additive attention (Bahdanau et al. 2015):$s_i=u^T\text{tanh}(A\vec{h}_i+B\vec{q})$
		2. Bilinear attention (Luong et al., 2015): $s_i=\vec{q}^TU\vec{h}_i$
		3. Dot product attention (Luong et al. 2015): particular case of bilinear attention; queries and keys must have the same size, $s_i=\vec{q}^T\vec{h}_i$. $O(n^2)$ complexity.
		4. Linear attention. $O(N)$ complexity [4].
		5. $\text{MLP}(q, \vec{h}_i)$.
	3. The input vectors $H=\begin{bmatrix}\vec{h_1},\ldots,\vec{h_L}\end{bmatrix}$ appear in two places:
		1. They are used as keys to "compare" them with the query vector $\vec{q}$ to obtain the affinity scores.
		2. They are used as values to form the weighted average $\vec{c}=H^T\vec{p}$.
	4. To be fully general, they don't have to be the same -- we can have:
		1. A key matrix 

References:
1. Formal Algorithms for Transformers, Mary Phuong, Marcus Hutter.
2. https://peterbloem.nl/blog/transformers
3. self attention vs fully connected layer. 
4. Transformers are RNNs: Fast Autoregressive Transformers with Linear Attention, Angelos Karthapoulos.
5. Effective Approaches to Attention-based Neural Machine Translation. Minh-Thang Luong.