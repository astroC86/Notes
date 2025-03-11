
# Finite Element Gradients with Inverse Jacobian Transformation

The equations are revised to explicitly reflect that $H_e$ is the **inverse Jacobian matrix** ($\mathbf{J}^{-1}$), which transforms derivatives from reference coordinates ($\xi, \eta, \zeta$) to physical coordinates ($x, y, z$). The code computes $H_e$ as $\mathbf{J}^{-1}$, derived from the adjugate matrix and determinant of the Jacobian $\mathbf{J}$.

---

## **Scalar Gradients**
For each `idime ∈ {1,2,3}` and `ii ∈ {1, ..., porder+1}`:

### **XI Direction Contributions (ξ):**
$$
\begin{aligned}
\text{gradRho}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot \rho_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\text{gradP}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot P_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\text{gradE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot E_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\text{gradRE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot RE_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\text{gradk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot k_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\text{gradRk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot Rk_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \\
\end{aligned}
$$

### **ETA Direction Contributions (η):**
$$
\begin{aligned}
\text{gradRho}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot \rho_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\text{gradP}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot P_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\text{gradE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot E_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\text{gradRE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot RE_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\text{gradk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot k_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\text{gradRk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot Rk_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \\
\end{aligned}
$$

### **ZETA Direction Contributions (ζ):**
$$
\begin{aligned}
\text{gradRho}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot \rho_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\text{gradP}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot P_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\text{gradE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot E_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\text{gradRE}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot RE_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\text{gradk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot k_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\text{gradRk}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot Rk_l(\text{invAtoIJK}_c(I, J, \text{ii})) \\
\end{aligned}
$$

---

## **Vector Gradients**
For each `idime, jdime ∈ {1,2,3}` and `ii ∈ {1, ..., porder+1}`:

### **XI Direction Contributions (ξ):**
$$
\begin{aligned}
\text{gradU}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\text{gradQ}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot Q_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\end{aligned}
$$

### **ETA Direction Contributions (η):**
$$
\begin{aligned}
\text{gradU}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\text{gradQ}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot Q_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\end{aligned}
$$

### **ZETA Direction Contributions (ζ):**
$$
\begin{aligned}
\text{gradU}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\text{gradQ}_{\text{idime},\text{jdime}} &+= \left[ \mathbf{J}^{-1}(\text{jdime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot Q_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\end{aligned}
$$

---

## **Divergence Terms**
For each `idime ∈ {1,2,3}` and `ii ∈ {1, ..., porder+1}`:

### **XI Direction Contributions (ξ):**
$$
\begin{aligned}
\text{divFe} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot \rho_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot E_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\text{divFue} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot E_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\text{divFk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot \rho_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot k_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\text{divFuk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot k_l(\text{invAtoIJK}_c(\text{ii}, J, K)) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \\
\text{divF}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot Q_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 1, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{jdime}) \\
\text{divFuu}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 1, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \xi} \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 1, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(\text{ii}, J, K), \text{jdime}) \\
\end{aligned}
$$

### **ETA Direction Contributions (η):**
$$
\begin{aligned}
\text{divFe} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot \rho_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot E_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\text{divFue} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot E_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\text{divFk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot \rho_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot k_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\text{divFuk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot k_l(\text{invAtoIJK}_c(I, \text{ii}, K)) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \\
\text{divF}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot Q_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 2, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{jdime}) \\
\text{divFuu}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 2, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \eta} \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 2, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(I, \text{ii}, K), \text{jdime}) \\
\end{aligned}
$$

### **ZETA Direction Contributions (ζ):**
$$
\begin{aligned}
\text{divFe} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot \rho_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot E_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\text{divFue} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot E_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\text{divFk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot \rho_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot k_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\text{divFuk} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot k_l(\text{invAtoIJK}_c(I, J, \text{ii})) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \\
\text{divF}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot Q_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 3, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{jdime}) \\
\text{divFuu}_{\text{idime}} &+= \left[ \mathbf{J}^{-1}(\text{idime}, 3, \text{igaus}, \text{ielem}) \right] \cdot \frac{\partial N_{\text{ii}}}{\partial \zeta} \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{idime}) \cdot \sum_{\text{jdime}=1}^3 \mathbf{J}^{-1}(\text{jdime}, 3, \text{igaus}, \text{ielem}) \cdot u_l(\text{invAtoIJK}_c(I, J, \text{ii}), \text{jdime}) \\
\end{aligned}
$$

---

## **Key Notation**
- $\mathbf{J}^{-1}(\text{idime}, \text{dir}, \text{igaus}, \text{ielem})$: Entry ($\text{idime}, \text{dir}$) of the inverse Jacobian matrix for Gauss point `igaus` and element `ielem` (dir = 1: ξ, 2: η, 3: ζ).
- $\frac{\partial N_{\text{ii}}}{\partial \xi}$, $\frac{\partial N_{\text{ii}}}{\partial \eta}$, $\frac{\partial N_{\text{ii}}}{\partial \zeta}$: Derivatives of the shape function $N_{\text{ii}}$ with respect to reference coordinates (stored in `dlxi_ip`, `dleta_ip`, `dlzeta_ip`).
- $\text{invAtoIJK}_c$: Maps the 1D index `ii` to 3D grid indices for the current direction (e.g., `invAtoIJK_c(ii, J, K)` fixes $J, K$ for the ξ direction).

The equations now explicitly show the role of the inverse Jacobian in transforming derivatives from the reference coordinate system to the physical domain.


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMDQwMTI3OTBdfQ==
-->