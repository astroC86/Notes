### 1. Velocity Divergence (∇·u)
$$\nabla \cdot \mathbf{u} = \frac{\partial u}{\partial x} + \frac{\partial v}{\partial y} + \frac{\partial w}{\partial z}$$

Code arrays:
- Stored in `divU(npoin)`
- Computed from:
  - `gradu_e(1,1) + gradu_e(2,2) + gradu_e(3,3)` for velocity divergence
  - `gradIsoRU` for momentum divergence

### 2. Velocity Curl (∇×u)
$$\nabla \times \mathbf{u} = \begin{pmatrix}
\frac{\partial w}{\partial y} - \frac{\partial v}{\partial z} \\
\frac{\partial u}{\partial z} - \frac{\partial w}{\partial x} \\
\frac{\partial v}{\partial x} - \frac{\partial u}{\partial y}
\end{pmatrix}$$

Code arrays:
- Stored in `curlU(npoin,ndime)`
- Computed using:
  - `leviCivi(idime,jdime,kdime)`: Levi-Civita tensor εijk
  - `gradu_e(jdime,kdime)`: Velocity gradients ∂uj/∂xk

### 3. Density Gradient (∇ρ)
$$\nabla \rho = \begin{pmatrix}
\frac{\partial \rho}{\partial x} \\
\frac{\partial \rho}{\partial y} \\
\frac{\partial \rho}{\partial z}
\end{pmatrix}$$

Code arrays:
- Stored in `gradRho(npoin,ndime)`
- Computed from:
  - `gradIsoRho(ndime)`: Local density gradients
  - Transformed using `He(idime,jdime,igaus,ielem)`

### 4. Q-criterion
$$Q = -\frac{1}{2}\sum_{i,j} \frac{\partial u_i}{\partial x_j} \frac{\partial u_j}{\partial x_i}$$

Code arrays:
- Stored in `Qcrit(npoin)`
- Computed using:
  - `gradu_e(idime,jdime)`: Velocity gradients ∂ui/∂xj
  - `gradu_e(jdime,idime)`: Transposed gradients ∂uj/∂xi

Input variables:
- `rho(npoin)`: Density field ρ
- `u(npoin,ndime)`: Velocity components (u,v,w)
- `He(ndime,ndime,ngaus,nelem)`: Metric tensor for coordinate transformation
- `dNgp(ndime,nnode,ngaus)`: Shape function derivatives at quadrature points
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyNjM0NzY1MV19
-->