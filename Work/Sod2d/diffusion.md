The `full_diffusion_ijk` subroutine computes the residuals for mass, momentum, and energy equations due to diffusion processes. The governing equations at each Gauss point are:

These integrals are discretized using finite elements with shape functions $N$ and Gauss quadrature, incorporating gradients transformed via the inverse Jacobian $H_e$. The contributions are accumulated atomically to handle parallel computation.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYwOTQ3MzY1MywyMTM1NDQ4MTE3XX0=
-->