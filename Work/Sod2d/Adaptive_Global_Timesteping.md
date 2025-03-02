**1. Characteristic Element Length:**
$h_e$ is the length of the element
$$L_e = \frac{h_e}{2p + 1}$$

**2. Convective Limit:**

Define the effective speed at each node $i$ in element $e$ as

$$L3_e = \max_{i \in e} \{ \max (|u_{i,1}|, |u_{i,2}|, |u_{i,3}|) + c_{sound,i} \}$$

Then, the convective time step for element $e$ is given by

$$\Delta t_{conv}^{(e)} = \text{cfl\_conv} \cdot \frac{L_e}{L3_e}$$

**3. Diffusive Limit (when provided):**

First, compute an effective viscosity at element $e$:

$$\mu_{eff}^{(e)} = \max_{i \in e} \left\{ \frac{\mu_{gas} + \mu_{fluid} + \mu_c}{\rho} \right\}$$

Then, the diffusive time step is

$$\Delta t_{diff}^{(e)} = \text{cfl\_diff} \cdot \frac{L_e^2}{\mu_{eff}^{(e)}}$$

 **4. Local and Global Time Step:**

For each element, the local time step is

$$\Delta t^{(e)} = \min \{ \Delta t_{conv}^{(e)}, \Delta t_{diff}^{(e)} \}$$

Finally, the global time step is determined as

$$\Delta t = \min_{e} \{ \Delta t^{(e)} \}$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NDUzODU5NDFdfQ==
-->