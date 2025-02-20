# Boundary Conditions in Electrostatics

When solving differential equations (like the **Poisson equation**), boundary conditions define how the potential $\phi(\mathbf{r})$ behaves at the edges of a region (like a cube or cylinder).

1. **Neumann Boundary Condition**

  - You fix the **derivative** of $\phi$ at the boundary:
    
    $$\frac{\partial \phi}{\partial n} = \text{constant}$$
  
  - This is useful when dealing with a **fixed charge on a surface**.

2. **Dirichlet Boundary Condition**

  - You fix the **value** of $\phi$ at the boundary:
    
    $$\phi(\mathbf{r}) = \text{constant}$$
  
  - Example: A **capacitor** where one plate is at 0V and another at 5V.

3. **Robin Boundary Condition**

  - A combination of both Neumann and Dirichlet conditions.

## Real-Life Applications

- **Electrostatics**:

 - **Neumann BC** → Used when there's a fixed charge on a surface.
 
 - **Dirichlet BC** → Used when a plate is connected to a **voltage source** (e.g., capacitors).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjc4MTg5MzBdfQ==
-->