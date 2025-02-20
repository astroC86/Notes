# The $d$th-order Taylor polynomial


The $d$th-order Taylor polynomial for a scalar-valued function $f : \mathbb{R}^n \to \mathbb{R}$ at a point $\mathbf{a}$ can be expressed as:

$$T_d(\mathbf{x}) = \sum_{k=0}^d \frac{1}{k!} \sum_{i_1,i_2,\dots,i_k} \frac{\partial^k f}{\partial x_{i_1}\partial x_{i_2}\cdots\partial x_{i_k}}(\mathbf{a})(x_{i_1} - a_{i_1})(x_{i_2} - a_{i_2})\cdots(x_{i_k} - a_{i_k}).$$

## Compact Notation Using Multi-Index

Using multi-index notation, where $\alpha = (\alpha_1,\alpha_2,\dots,\alpha_n)$ is a multi-index and $|\alpha| = \sum_i \alpha_i$, we write:

$$T_d(\mathbf{x}) = \sum_{|\alpha|\leq d} \frac{D^\alpha f(\mathbf{a})}{\alpha!}(\mathbf{x}-\mathbf{a})^\alpha.$$

Where:

- $D^\alpha f = \frac{\partial^{|\alpha|}f}{\partial x_1^{\alpha_1}\partial x_2^{\alpha_2}\cdots\partial x_n^{\alpha_n}}$ is the partial derivative.
- $\alpha! = \alpha_1!\alpha_2!\cdots\alpha_n!$
- $(\mathbf{x}-\mathbf{a})^\alpha = (x_1-a_1)^{\alpha_1}(x_2-a_2)^{\alpha_2}\cdots(x_n-a_n)^{\alpha_n}$

## Matrix/Tensor Formulation

Rewriting using vector notation with $\mathbf{h} = \mathbf{x} - \mathbf{a}$:

$$T_d(\mathbf{x}) = \sum_{k=0}^d \frac{1}{k!}\nabla^k f(\mathbf{a})\cdot(\mathbf{h}^{\otimes k}).$$

Where:

- $\nabla^k f(\mathbf{a})$ is the $k$th-order derivative tensor.
- $\mathbf{h}^{\otimes k}$ is the $k$th-order outer product of $\mathbf{h}$.
- The contraction $\cdot$ denotes the summation over tensor indices.

This generalizes the scalar $(d=0)$, gradient $(d=1)$, Hessian $(d=2)$, and third-order tensor $(d=3)$ expressions.


## Example Function:

Consider the function:
$$f(x,y) = e^x \sin y$$

We will compute its third-order Taylor expansion around the point $(a,b) = (0,0)$.

### Step 1: Compute Partial Derivatives

We first compute the partial derivatives up to the third order.

#### Zeroth Order (Function Value)
$$f(0,0) = e^x \sin 0 = 0.$$

#### First-Order Derivatives (Gradient)
$$\frac{\partial f}{\partial x} = e^x \sin y, \quad \frac{\partial f}{\partial y} = e^x \cos y.$$

At $(0,0)$:
$$\nabla f(0,0) = \begin{bmatrix} \sin 0 \\ \cos 0 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \end{bmatrix}.$$

#### Second-Order Derivatives (Hessian)
$$\frac{\partial^2 f}{\partial x^2} = e^x \sin y, \quad \frac{\partial^2 f}{\partial y^2} = -e^x \sin y, \quad \frac{\partial^2 f}{\partial x\partial y} = e^x \cos y.$$

At $(0,0)$:
$$H_f(0,0) = \begin{bmatrix} \sin 0 & \cos 0 \\ \cos 0 & -\sin 0 \end{bmatrix} = \begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}.$$

## Third-Order Derivatives (Third-Order Tensor)

We compute the third-order derivatives:
$$\frac{\partial^3 f}{\partial x^3} = e^x \sin y, \quad \frac{\partial^3 f}{\partial y^3} = -e^x \cos y, \quad \frac{\partial^3 f}{\partial x^2\partial y} = e^x \cos y, \quad \frac{\partial^3 f}{\partial x\partial y^2} = -e^x \cos y.$$

At $(0,0)$:
$$\frac{\partial^3 f}{\partial x^3} = 0, \quad \frac{\partial^3 f}{\partial y^3} = -1, \quad \frac{\partial^3 f}{\partial x^2\partial y} = 1, \quad \frac{\partial^3 f}{\partial x\partial y^2} = -1.$$

Thus, the third-order tensor (nonzero elements) is:

$$\nabla^3f(0,0) = \begin{array}{c|ccc} 
& (x^2y) & (xy^2) & (y^3) \\
\hline
\text{Coefficient} & 1 & -1 & -1
\end{array}$$

### Step 2: Compute the Taylor Expansion

Using the formula:
$$T_3(x,y) = f(0,0) + \nabla f(0,0) \cdot \mathbf{h} + \frac{1}{2}\mathbf{h}^T H_f(0,0)\mathbf{h} + \frac{1}{6}\nabla^3f(0,0) \cdot \mathbf{h}^{\otimes 3}.$$

Substituting:

1. Zeroth-order term: $0$.

2. First-order term:
  $$0(x-0) + 1(y-0) = y.$$

3. Second-order term:
  $$\frac{1}{2}[x \quad y]\begin{bmatrix}0 & 1\\1 & 0\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix} = \frac{1}{2}(2xy) = xy.$$

4. Third-order term:
  $$\frac{1}{6}((x^2y) - (xy^2) - y^3).$$

### Final Expression:
$$T_3(x,y) = y + xy + \frac{1}{6}(x^2y - xy^2 - y^3).$$

### Interpretation of the Outer Product

For the third-order term, the outer product $\mathbf{h}^{\otimes 3}$ is:
$$\mathbf{h}^{\otimes 3} = \begin{bmatrix}x\\y\end{bmatrix} \otimes \begin{bmatrix}x\\y\end{bmatrix} \otimes \begin{bmatrix}x\\y\end{bmatrix}.$$

This creates a rank-3 tensor where each entry is a monomial of degree 3 in $x,y$:
$$\mathbf{h}^{\otimes 3} = \begin{bmatrix}
(x^3, x^2y, xy^2, y^3)\\
(x^2y, xy^2, y^3, xy^2)
\end{bmatrix}.$$

This structure contracts with the third derivative tensor to form the cubic terms in the expansion.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTkyODc1ODldfQ==
-->