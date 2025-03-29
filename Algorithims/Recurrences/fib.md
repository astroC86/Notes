We start with the recurrence
$T(n) = T(n-1) + T(n-2) + O(1)$

For clarity, let's replace the $O(1)$ term by a constant $c$ (the analysis will be the same if it's any constant). That is, we consider
$T(n) = T(n-1) + T(n-2) + c$.

The standard method is to first solve the homogeneous part and then find a particular solution.

#1. Solve the Homogeneous Recurrence

The homogeneous recurrence is
$T_h(n) = T_h(n-1) + T_h(n-2)$.

Assume a solution of the form
$T_h(n) = r^n$.

Substitute into the homogeneous recurrence:
$r^n = r^{n-1} + r^{n-2}$.

Dividing both sides by $r^{n-2}$ (assuming $r \neq 0$) gives
$r^2 = r + 1$.

Rearrange into the characteristic equation:
$r^2 - r - 1 = 0$.

Solve this quadratic equation using the quadratic formula:
$r = \frac{1 \pm \sqrt{1 + 4}}{2} = \frac{1 \pm \sqrt{5}}{2}$.

Thus, the two roots are
$r_1 = \phi = \frac{1+\sqrt{5}}{2} \quad \text{and} \quad r_2 = \psi = \frac{1-\sqrt{5}}{2}$.

The general solution for the homogeneous part is
$T_h(n) = A \phi^n + B \psi^n$,

where $A$ and $B$ are constants determined by initial conditions.

### 2. Find a Particular Solution

Now we need a particular solution $T_p(n)$ to the non-homogeneous recurrence
$T(n) = T(n-1) + T(n-2) + c$.

A good starting guess is a constant solution. Assume
$T_p(n) = D$,

where $D$ is a constant. Substituting into the recurrence:
$D = D + D + c$,
$D = 2D + c$.

Solving for $D$:
$D - 2D = c \quad \Rightarrow \quad -D = c \quad \Rightarrow \quad D = -c$.

Thus, a particular solution is
$T_p(n) = -c$.

### 3. Write the General Solution

The general solution to the recurrence is the sum of the homogeneous and particular solutions:
$T(n) = T_h(n) + T_p(n) = A \phi^n + B \psi^n - c$.

Since $\phi = \frac{1+\sqrt{5}}{2} \approx 1.618$ and $|\psi| = \left|\frac{1-\sqrt{5}}{2}\right| \approx 0.618 < 1$, for large $n$ the term $B \psi^n$ becomes negligible, and the solution is dominated by the $\phi^n$ term.

Thus, we can conclude that
$T(n) = \Theta(\phi^n)$,

which means the recurrence grows exponentially with base $\phi$.

### 4. Summary of Steps

1. **Homogeneous Solution:**
   * Assume $T_h(n) = r^n$.
   * Obtain the characteristic equation: $r^2 - r - 1 = 0$.
   * Solve to get $r_1 = \phi = \frac{1+\sqrt{5}}{2}$ and $r_2 = \psi = \frac{1-\sqrt{5}}{2}$.
   * Write $T_h(n) = A \phi^n + B \psi^n$.

2. **Particular Solution:**
   * Guess $T_p(n) = D$ (a constant).
   * Substitute to find $D = -c$.

3. **General Solution:**
   * Combine to get $T(n) = A \phi^n + B \psi^n - c$.
   * As $n$ increases, $T(n) \sim \Theta(\phi^n)$.

### Final Answer

The solution to the recurrence
$T(n) = T(n-1) + T(n-2) + O(1)$

is
$T(n) = A \left(\frac{1+\sqrt{5}}{2}\right)^n + B \left(\frac{1-\sqrt{5}}{2}\right)^n - c$,

which asymptotically gives
$T(n) = \Theta\!\left(\left(\frac{1+\sqrt{5}}{2}\right)^n\right)$.

This completes the solution.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4OTc1NjAzMjJdfQ==
-->