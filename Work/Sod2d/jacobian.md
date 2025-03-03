The code computes the element‐level Jacobian matrix for each Gauss integration point, its determinant, and then the inverse Jacobian. Here's how the operations can be written mathematically:

## 1. Jacobian Matrix Calculation
For a given element (indexed by $ielem$) and Gauss point (indexed by $igaus$), the $2×2$ Jacobian matrix $\mathbf{J}$ is computed by summing over the element's nodes:

$$J_{ij} = \sum_{inode=1}^{nnode} \left( \frac{\partial N_{inode}}{\partial \xi_i} (\text{igaus}) \right) \, x_{\text{node}(inode), j} \quad \text{for } i,j=1,2$$

where:
* $\frac{\partial N_{inode}}{\partial \xi_i} (\text{igaus})$ corresponds to `dNgp(idime, inode, igaus)` (the derivative of the shape function with respect to the $i$-th parametric coordinate),
* $x_{\text{node}(inode), j}$ corresponds to `coord(node, jdime)`, with `node = connec(ielem, inode)`.

In matrix form, the Jacobian is:

$$\mathbf{J} = \begin{bmatrix} J_{11} & J_{12} \\ J_{21} & J_{22} \end{bmatrix}$$

## 2. Gauss Point Volume Factor
The Gauss point volume (accounting for the weight $w_{igaus}$) is computed using the determinant of $\mathbf{J}$:

$$gpvol(igaus, ielem) = w_{igaus} \cdot \det(\mathbf{J}) = w_{igaus} \cdot \left( J_{11}\,J_{22} - J_{21}\,J_{12} \right)$$

## 3. Inverse Determinant
To invert the Jacobian, the code first computes the inverse of its determinant:

$$inv\_det = \frac{1}{\det(\mathbf{J})} = \frac{1}{J_{11}\,J_{22} - J_{21}\,J_{12}}$$

*(Note: In the code, $\det(\mathbf{J})$ is recovered by dividing $gpvol$ by $w_{igaus}$.)*

## 4. Inverse Jacobian Matrix
Finally, the inverse of a $2×2$ matrix $\mathbf{J}$ is given by:

$$\mathbf{J}^{-1} = \frac{1}{\det(\mathbf{J})} \begin{bmatrix} J_{22} & -J_{12} \\ -J_{21} & J_{11} \end{bmatrix}$$

Thus, the components stored in the array `He` are:

$$\begin{aligned} 
He(1,1,igaus,ielem) &= J_{22} \cdot inv\_det, \\ 
He(1,2,igaus,ielem) &= -J_{12} \cdot inv\_det, \\ 
He(2,1,igaus,ielem) &= -J_{21} \cdot inv\_det, \\ 
He(2,2,igaus,ielem) &= J_{11} \cdot inv\_det. 
\end{aligned}$$

These equations fully describe the operations performed in the provided code.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQ5MTgyMTQzXX0=
-->