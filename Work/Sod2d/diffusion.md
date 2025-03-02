The `full_diffusion_ijk` subroutine computes the residuals for mass, momentum, and energy equations due to diffusion processes. The governing equations at each Gauss point are:
1. **Stress Tensor (Momentum Diffusion)**:
   $$
   \tau_{ij} = (\mu_{\text{fluid}} + \rho_n \mu_{\text{sgs}} + \mu_e) \left( \frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i} \right) - \frac{2}{3} (\mu_{\text{fluid}} + \rho_n \mu_{\text{sgs}}) \delta_{ij} \nabla \cdot \mathbf{u}
   $$
   where $\mu_{\text{total}} = \mu_{\text{fluid}} + \rho_n \mu_{\text{sgs}} + \mu_e$.
2. **Heat Flux (Energy Diffusion)**:
   $$
   q_i = -\kappa_{\text{total}} \frac{\partial T}{\partial x_i}
   $$
   with thermal conductivity:
   $$
   \kappa_{\text{total}} = \frac{\mu_{\text{fluid}} C_p}{Pr} + \frac{c_{\text{ener}} \mu_e C_p}{Pr} + \frac{C_p \rho_n \mu_{\text{sgs}}}{0.9}
   $$
3. **Mass Diffusion (Stabilization)**:
   $$
   \text{Contribution: } \nu_e \nabla^2 \rho \quad \text{where } \nu_e = \frac{c_{\rho} \mu_e}{\rho_n}
   $$
The residuals are integrated over elements and assembled as:
- **Mass Residual**:
  $$
  R_{\text{mass}}^i \leftarrow R_{\text{mass}}^i + \int_{\Omega} \nu_e \nabla^2 \rho \, d\Omega
  $$
- **Momentum Residual**:
  $$
  R_{\text{mom}}^i \leftarrow R_{\text{mom}}^i + \int_{\Omega} \nabla \cdot \boldsymbol{\tau} \, d\Omega
  $$
- **Energy Residual**:
  $$
  R_{\text{ener}}^i \leftarrow R_{\text{ener}}^i + \int_{\Omega} \nabla \cdot \left( \boldsymbol{\tau} \cdot \mathbf{u} - \kappa_{\text{total}} \nabla T \right) \, d\Omega
  $$
These integrals are discretized using finite elements with shape functions $N$ and Gauss quadrature, incorporating gradients transformed via the inverse Jacobian $H_e$. The contributions are accumulated atomically to handle parallel computation.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEzNTQ0ODExN119
-->