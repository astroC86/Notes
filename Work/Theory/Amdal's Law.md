# Amdahl's Law for Program Speedup
## Multiple Portions

Let:
- **$p$** be the fraction of the program's run time that is sped up (expressed as a decimal; for example, 40% → 0.40),
- **$S$** be the factor by which that portion is sped up.

### Step-by-Step Calculation

1. **Original Run Time:**  
   Assume the original run time is $T$.

2. **New Run Time After Speedup:**  
   - The part that is not sped up takes $(1-p)T$ time.
   - The sped-up part now takes $\frac{pT}{S}$ time.  
     
   So the total new time is:  
   $$
   T' = (1-p)T + \frac{pT}{S}
   $$

3. **Overall Time Reduction:**  
   The reduction in time is:
   $$
   \Delta T = T - T' = T - \left[(1-p)T + \frac{pT}{S}\right]
   $$
   Factor out $T$:
   $$
   \Delta T = T\left[1 - \left((1-p) + \frac{p}{S}\right)\right]
   $$
   Simplify the bracket:
   $$
   \Delta T = T\left[p - \frac{p}{S}\right] = T \cdot p\left(1-\frac{1}{S}\right)
   $$

4. **Percentage Time Reduction:**  
   To express this reduction as a percentage of the original time:
   $$
   \text{Percentage Time Reduction} = \frac{\Delta T}{T} \times 100\% = p\left(1-\frac{1}{S}\right) \times 100\%
   $$

### Example

If 40% of the program ($p = 0.40$) is sped up by a factor of 4 ($S = 4$):
$$
\text{Percentage Time Reduction} = 0.40 \times \left(1 - \frac{1}{4}\right) \times 100\% = 0.40 \times 0.75 \times 100\% = 30\%
$$

### Final Answer

The overall percentage time reduction is calculated as:
$$
\boxed{100\% \times p \left(1-\frac{1}{S}\right)}
$$
where $p$ is the fraction of the program that is sped up, and $S$ is the speedup factor.

## Multiple Portions


When you have multiple portions of a program that are sped up by different factors, you can generalize the single-portion formula by breaking the program into parts. Here's how:

## Definitions
* Let $p_i$ be the fraction of the total original execution time taken by portion $i$ (with $\sum_i p_i \le 1$).
* Let $S_i$ be the speedup factor for portion $i$.

## Calculating the New Execution Time
The original execution time is $T$. After applying the speedups:
* **Portions with speedup:** Each portion $i$ now takes $\frac{p_i T}{S_i}$.
* **Unchanged portion:** If there's any part of the program that isn't sped up, it takes $\left(1 - \sum_i p_i\right)T$.

So, the new total execution time is:
$$T' = T\left[\left(1 - \sum_i p_i\right) + \sum_i \frac{p_i}{S_i}\right]$$

## Overall Time Reduction
The reduction in time, $\Delta T$, is:
$$\Delta T = T - T' = T\left[1 - \left(\left(1 - \sum_i p_i\right) + \sum_i \frac{p_i}{S_i}\right)\right]$$

## Percentage Time Reduction
To express the time reduction as a percentage of the original time:
$$\text{Percentage Reduction} = \left(1 - \left[\left(1 - \sum_i p_i\right) + \sum_i \frac{p_i}{S_i}\right]\right) \times 100\%$$

## Example
Suppose you have two portions:
* Portion 1: $p_1 = 0.3$ (30% of the time) with a speedup $S_1 = 3$.
* Portion 2: $p_2 = 0.4$ (40% of the time) with a speedup $S_2 = 2$.

1. **New Time Calculation:** $T' = T\left[\left(1 - (0.3+0.4)\right) + \frac{0.3}{3} + \frac{0.4}{2}\right] = T\left[0.3 + 0.1 + 0.2\right] = T(0.6)$
2. **Time Reduction:** $\Delta T = T - 0.6T = 0.4T$
3. **Percentage Reduction:** $0.4T / T \times 100\% = 40\%$


For multiple portions sped up by different factors, the overall percentage time reduction is given by:
$$\boxed{\text{Percentage Reduction} = \left(1 - \left[\left(1 - \sum_i p_i\right) + \sum_i \frac{p_i}{S_i}\right]\right) \times 100\%}$$

This formula accounts for both the accelerated and the non-accelerated parts of your program.
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYxOTQzODY3NF19
-->