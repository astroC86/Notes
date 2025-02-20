The $k$th-order outer product of a vector $\mathbf{h} \in \mathbb{R}^n$ is a higher-order tensor constructed by taking the outer product of $\mathbf{h}$ with itself $k$ times.

# Definition:

The $k$-th order outer product of $\mathbf{h}$ is given by:

$$\mathbf{h}^{\otimes k} = \underbrace{\mathbf{h} \otimes \mathbf{h} \otimes \cdots \otimes \mathbf{h}}_{k \text{ times}}$$

where $\otimes$ denotes the outer product.

# Component-wise Expression:

If $\mathbf{h} = (h_1, h_2, \ldots, h_n) \in \mathbb{R}^n$, then $\mathbf{h}^{\otimes k}$ is an $n \times n \times \cdots \times n$ ($k$ times) tensor whose entries are:

$$(\mathbf{h}^{\otimes k})_{i_1,\ldots,i_k} = h_{i_1}h_{i_2}\cdots h_{i_k}, \quad \text{for } i_1, i_2, \ldots, i_k \in \{1,\ldots,n\}.$$

# Examples:

1. First-order case $(k = 1)$:
  $$\mathbf{h}^{\otimes 1} = \mathbf{h} = (h_1, h_2, \ldots, h_n).$$

2. Second-order case $(k = 2)$: The outer product $\mathbf{h} \otimes \mathbf{h}$ results in an $n \times n$ matrix:
  $$(\mathbf{h} \otimes \mathbf{h})_{ij} = h_ih_j.$$

3. Third-order case $(k = 3)$: The outer product $\mathbf{h} \otimes \mathbf{h} \otimes \mathbf{h}$ results in an $n \times n \times n$ tensor:
  $$(\mathbf{h}^{\otimes 3})_{ijk} = h_ih_jh_k.$$

# Usage in Taylor Expansion:

In the Taylor series of multiple variables, the $k$th-order term involves the contraction of the $k$th-order derivative tensor $\nabla^k f$ with $\mathbf{h}^{\otimes k}$:

$$\frac{1}{k!}\nabla^k f(\mathbf{a}) \cdot \mathbf{h}^{\otimes k}.$$

Here, the contraction $\cdot$ means summing over repeated indices:

$$\frac{1}{k!} \sum_{i_1,\ldots,i_k} \frac{\partial^k f}{\partial x_{i_1}\partial x_{i_2}\cdots\partial x_{i_k}}(\mathbf{a})h_{i_1}h_{i_2}\cdots h_{i_k}.$$

This generalizes the usual Hessian quadratic form, where for $k = 2$:

$$\frac{1}{2}\mathbf{h}^T H(\mathbf{a})\mathbf{h}.$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzU0NTM3MDZdfQ==
-->