The `full_diffusion_ijk` subroutine computes the residuals for mass, momentum, and energy equations due to diffusion processes. The governing equations at each Gauss point are:

### **1. Stress Tensor (Momentum Diffusion):**
$$
\tau_{ij} = (\mu_{\text{fluid}} + \rho_n \mu_{\text{sgs}} + \mu_e) \left( \frac{\partial u_i}{\partial x_j} + \frac{\partial u_j}{\partial x_i} \right) - \frac{2}{3} (\mu_{\text{fluid}} + \rho_n \mu_{\text{sgs}}) \delta_{ij} \nabla \cdot \mathbf{u}
$$
- `tau(1:3,1:3)` : $\tau_{ij}$ (stress tensor components).  
- `mu_fluid(ipoin)` : $\mu_{\text{fluid}}$ (fluid dynamic viscosity).  
- `mu_sgs(ielem,igaus)` : $\mu_{\text{sgs}}$ (subgrid-scale viscosity).  
- `rho_n(ipoin)` : $\rho_n$ (density at previous timestep).  
- `mu_e(ielem,igaus)` : $\mu_e$ (eddy viscosity).  
- `gradU(1:3,1:3)` : $\frac{\partial u_i}{\partial x_j}$ (velocity gradient).  
- `divU` : $\nabla \cdot \mathbf{u}$ (velocity divergence).  
- `twoThirds` : $\frac{2}{3}$ (constant).  
---
### **2. Heat Flux (Energy Diffusion):**
$$
q_i = -\kappa_{\text{total}} \frac{\partial T}{\partial x_i}, \quad \kappa_{\text{total}} = \frac{\mu_{\text{fluid}} C_p}{Pr} + \frac{c_{\text{ener}} \mu_e C_p}{Pr} + \frac{C_p \rho_n \mu_{\text{sgs}}}{0.9}
$$
- `gradT(1:3)` : $\frac{\partial T}{\partial x_i}$ (temperature gradient).  
- `kappa_e` : $\kappa_{\text{total}}$ (total thermal conductivity).  
- `Cp` : $C_p$ (specific heat at constant pressure).  
- `Pr` : $Pr$ (Prandtl number).  
- `c_ener` : $c_{\text{ener}}$ (energy model constant).  
---
### **3. Mass Diffusion (Stabilization Term):**
$$
\nu_e \nabla^2 \rho, \quad \nu_e = \frac{c_{\rho} \mu_e}{\rho_n}
$$
- `nu_e` : $\nu_e$ (mass diffusion coefficient).  
- `c_rho` : $c_{\rho}$ (stabilization constant).  
- `gradRho(1:3)` : $\nabla \rho$ (density gradient).  
---
### **4. Residuals (RHS Contributions):**
- **Mass Residual**:
  $$
  R_{\text{mass}}^i \leftarrow R_{\text{mass}}^i + \int \nu_e \nabla^2 \rho \, d\Omega
  $$
  - `Rmass(ipoin)` : $R_{\text{mass}}^i$.  
  - `divDr` : $\int \nu_e \nabla^2 \rho \, d\Omega$.  
- **Momentum Residual**:
  $$
  R_{\text{mom}}^i \leftarrow R_{\text{mom}}^i + \int \nabla \cdot \boldsymbol{\tau} \, d\Omega
  $$
  - `Rmom(ipoin,1:3)` : $R_{\text{mom}}^i$.  
  - `divDm(1:3)` : $\int \nabla \cdot \boldsymbol{\tau} \, d\Omega$.  
- **Energy Residual**:
  $$
  R_{\text{ener}}^i \leftarrow R_{\text{ener}}^i + \int \nabla \cdot \left( \boldsymbol{\tau} \cdot \mathbf{u} - \kappa_{\text{total}} \nabla T \right) \, d\Omega
  $$
  - `Rener(ipoin)` : $R_{\text{ener}}^i$.  
  - `divDe` : $\int \nabla \cdot (\boldsymbol{\tau} \cdot \mathbf{u} - \kappa_{\text{total}} \nabla T) \, d\Omega$.  
---
### **5. Discretization Variables**:
- `He(1:3,1:3,igaus,ielem)` : Inverse Jacobian matrix for gradient transformations.  
- `gpvol(1,igaus,ielem)` : Gauss point volume ($d\Omega$).  
- `Ngp(igaus,inode)` : Shape functions at Gauss points.  
- `dlxigp_ip(igaus,idime,ii)` : Derivatives of shape functions in reference coordinates.  
- `invAtoIJK` : Maps Gauss points to IJK-structured nodes.  
---
### **6. Other Key Variables**:
- `ul(1:nnode,1:3)` : Local velocity vector $\mathbf{u}$.  
- `Teml(1:nnode)` : Local temperature $T$.  
- `rhol(1:nnode)` : Local density $\rho$.  
- `aux_fact` : Scaling factor for residuals (e.g., time integration).  
This mapping connects the **numerical implementation** (variables in the code) to the **mathematical symbols** in the governing equations.

These integrals are discretized using finite elements with shape functions $N$ and Gauss quadrature, incorporating gradients transformed via the inverse Jacobian $H_e$. The contributions are accumulated atomically to handle parallel computation.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQyNTc1NjAxNiwyMTM1NDQ4MTE3XX0=
-->