
A general multidimensional quadratic equation can be written in matrix form as
$$x^T A x + b^T x + c = 0,$$
where:
- $x$ is an $n \times 1$ column vector of variables, i.e., $x = (x_1, x_2, \dots, x_n)^T$.
- $A$ is an $n \times n$ matrix (usually assumed to be symmetric for a well-defined quadratic form).
- $b$ is an $n \times 1$ vector.
- $c$ is a scalar constant.

In index notation, using the Einstein summation convention (which implies summation over repeated indices), the same equation is expressed as
$$A_{ij}\, x_i\, x_j + b_i\, x_i + c = 0,$$
with the indices $i$ and $j$ each running from 1 to $n$.

**Mapping Details:**
- The term $x^T A x$ in matrix notation expands to
    
    $$x^T A x = \sum_{i=1}^n \sum_{j=1}^n x_i\, A_{ij}\, x_j,$$
    
    which in Einstein summation convention is compactly written as $A_{ij}\, x_i\, x_j$.
    
- Similarly, the linear term $b^T x$ becomes
    
    $$b^T x = \sum_{i=1}^n b_i\, x_i,$$
    
    or simply $b_i\, x_i$ in index notation.
    
- The constant $c$ remains unchanged.
    
This mapping clearly shows how the quadratic form in multiple dimensions is represented in both matrix and index notation.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg3OTM5ODYyNV19
-->