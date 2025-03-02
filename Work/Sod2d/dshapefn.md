We can describe the computation of dlxigp_ip_r8 by first defining the Lagrange basis functions and their derivatives at an evaluation point, and then forming the triple–tensor product that naturally produces the derivative interpolation matrix.

Let  
$$
\{\xi_1,\xi_2,\dots,\xi_{p+1}\}
$$  
be the nodes (with $p = \text{mporder}$). In the code a reordering is applied via  
$$
\begin{aligned}
lorder(1) &= 1,\\[1mm]
lorder(2) &= p+1,\\[1mm]
lorder(i) &= i-1,\quad i=3,\dots,p+1.
\end{aligned}
$$

### 1. Lagrange Polynomials

For a given evaluation point $x$ (denoted by $\xi_p$ in the subroutines) the Lagrange basis function corresponding to the (reordered) node $i$ is defined as

$$
l_i(x) = \prod_{\substack{j=1 \\ j\neq lorder(i)}}^{p+1} \frac{x - \xi_j}{\xi_{lorder(i)} - \xi_j}\,.
$$

Its derivative is given by

$$
l'_i(x) = \sum_{\substack{j=1 \\ j\neq lorder(i)}}^{p+1} \frac{1}{\xi_{lorder(i)} - \xi_j}\, \prod_{\substack{m=1 \\ m\neq lorder(i),\,m\neq j}}^{p+1} \frac{x - \xi_m}{\xi_{lorder(i)} - \xi_m}\,.
$$

These equations correspond to the two subroutines **eval_lagrangePoly** and **eval_lagrangePolyDeriv**.

### 2. Triple Tensor Product

In the subroutine **TripleTensorProduct** the Lagrange polynomials are evaluated in three coordinate directions. For a given Gauss point with coordinates $(s,t,z)$ we define:

- In the $s$ (or $x$) direction:
  $$
  l^\xi_i(s) = l_i(s), \quad \text{and} \quad (l^\xi_i)'(s) = l'_i(s),
  $$
- In the $t$ (or $y$) direction:
  $$
  l^\eta_j(t) = l_j(t), \quad \text{and} \quad (l^\eta_j)'(t) = l'_j(t),
  $$
- In the $z$ direction:
  $$
  l^\zeta_k(z) = l_k(z), \quad \text{and} \quad (l^\zeta_k)'(z) = l'_k(z).
  $$

The shape function for a tensor–product element is then

$$
N_{ijk} = l^\xi_i(s)\, l^\eta_j(t)\, l^\zeta_k(z)\,,
$$

with its directional derivatives given by

$$
\begin{aligned}
\frac{\partial N_{ijk}}{\partial s} &= (l^\xi_i)'(s)\, l^\eta_j(t)\, l^\zeta_k(z),\\[1mm]
\frac{\partial N_{ijk}}{\partial t} &= l^\xi_i(s)\, (l^\eta_j)'(t)\, l^\zeta_k(z),\\[1mm]
\frac{\partial N_{ijk}}{\partial z} &= l^\xi_i(s)\, l^\eta_j(t)\, (l^\zeta_k)'(z).
\end{aligned}
$$

### 3. Computation of dlxigp_ip

Within **TripleTensorProduct**, the derivative Gauss–point interpolation matrix is formed by extracting the derivatives of the Lagrange polynomials in each coordinate direction. In other words, if we define

$$
\begin{aligned}
dlxigp\_ip(1,i) &= (l^\xi_i)'(s),\\[1mm]
dlxigp\_ip(2,i) &= (l^\eta_i)'(t),\\[1mm]
dlxigp\_ip(3,i) &= (l^\zeta_i)'(z),
\end{aligned}
$$
for $i = 1, \dots, p+1$, then the matrix $dlxigp\_ip$ (and ultimately its real version, $dlxigp\_ip\_r8$) is given by these rows.

In summary, using only equations, the procedure is:

1. **Compute the Lagrange basis and its derivative** for a given coordinate (say, $x$):

   $$
   l_i(x) = \prod_{\substack{j=1 \\ j\neq lorder(i)}}^{p+1} \frac{x - \xi_j}{\xi_{lorder(i)} - \xi_j}\quad\text{and}\quad
   l'_i(x) = \sum_{\substack{j=1 \\ j\neq lorder(i)}}^{p+1} \frac{1}{\xi_{lorder(i)} - \xi_j} \prod_{\substack{m=1 \\ m\neq lorder(i),\,m\neq j}}^{p+1} \frac{x - \xi_m}{\xi_{lorder(i)} - \xi_m}\,.
   $$

2. **Evaluate in three dimensions** (at $(s,t,z)$):

   $$
   \begin{aligned}
   N_{ijk} &= l_i(s)\, l_j(t)\, l_k(z),\\[1mm]
   \frac{\partial N_{ijk}}{\partial s} &= l'_i(s)\, l_j(t)\, l_k(z),\\[1mm]
   \frac{\partial N_{ijk}}{\partial t} &= l_i(s)\, l'_j(t)\, l_k(z),\\[1mm]
   \frac{\partial N_{ijk}}{\partial z} &= l_i(s)\, l_j(t)\, l'_k(z).
   \end{aligned}
   $$

3. **Assemble the derivative interpolation matrix:**

   $$
   \begin{aligned}
   dlxigp\_ip(1,i) &= l'_i(s),\\[1mm]
   dlxigp\_ip(2,i) &= l'_i(t),\\[1mm]
   dlxigp\_ip(3,i) &= l'_i(z),
   \end{aligned}
   $$
   for each $i = 1,\dots,p+1$. This matrix is then used in subsequent computations, and when converted to double precision (r8) becomes $dlxigp\_ip\_r8$.

---

**Symmetry Notice:**  
If the nodes $\xi_i$ are chosen from a symmetric distribution (as is the case for Gauss–Lobatto–Legendre nodes on $[-1,1]$), then the Lagrange basis functions satisfy  
$$
l_i(-x) = l_{p+2-i}(x),
$$
and their derivatives satisfy  
$$
l'_i(-x) = -\,l'_{p+2-i}(x).
$$
This symmetry is naturally inherited by the tensor–product construction and hence by the matrix $dlxigp\_ip\_r8$.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNjcyNzU5M119
-->