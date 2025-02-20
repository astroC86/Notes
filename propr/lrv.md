Below is one way to express the computations in the code as pseudocode that interleaves algorithmic steps with mathematical equations. In the following, let

- $(Y \in \mathbb{R}^{N\times p})$ be the data matrix (with $N$ observations and $p$ features).
- $(W \in \mathbb{R}^{N\times p})$ be the weight matrix.
- Optionally, $Y^{\text{full}}$ and $W^{\text{full}}$ are provided for scaling.
- $a$ is a parameter (if provided, we do an $\alpha$–transformation; if not, $a$ is treated as NA).
- The statistic is computed for each unordered pair $(i,j)$ with $1\le j < i\le p$.

The pseudocode below is organized by branch (depending on whether $a$ is provided and whether the weighted option is used):



---

### **Detailed Equations by Case**

#### **Case 1: $a$ is provided ($\alpha$–transformation)**

1. **Transformation:**
   $$
   X_{k,i} = Y_{k,i}^a,\quad X_{k,j} = Y_{k,j}^a,\quad
   X^{\text{full}}_{k,i} = \bigl(Y^{\text{full}}_{k,i}\bigr)^a,\quad X^{\text{full}}_{k,j} = \bigl(Y^{\text{full}}_{k,j}\bigr)^a.
   $$
   
2. **Weighted Version:**
   - **Weights:**
     $$
     w_k = W_{k,i} \, W_{k,j},\quad w_k^{\text{full}} = W^{\text{full}}_{k,i} \, W^{\text{full}}_{k,j}.
     $$
   - **Weighted Means:**
     $$
     \mu_i = \frac{\sum_{k=1}^N w_k\, X_{k,i}}{\sum_{k=1}^N w_k},\quad \mu_j = \frac{\sum_{k=1}^N w_k\, X_{k,j}}{\sum_{k=1}^N w_k},
     $$
     $$
     m_i = \frac{\sum_{k=1}^N w_k^{\text{full}}\, X^{\text{full}}_{k,i}}{\sum_{k=1}^N w_k^{\text{full}}},\quad m_j = \frac{\sum_{k=1}^N w_k^{\text{full}}\, X^{\text{full}}_{k,j}}{\sum_{k=1}^N w_k^{\text{full}}}.
     $$
   - **Centering and Scaling:**
     $$
     d_{k,i} = \frac{X_{k,i} - \mu_i}{m_i},\quad d_{k,j} = \frac{X_{k,j} - \mu_j}{m_j}.
     $$
   - **lrv Computation:**
     $$
     \text{Numerator} = \sum_{k=1}^N w_k\,\bigl(d_{k,i} - d_{k,j}\bigr)^2,
     $$
     where
     $$
     S = \sum_{k=1}^N w_k,\quad Q = \sum_{k=1}^N w_k^2.
     $$
     Then,
     $$
     \operatorname{lrv}_{ij} = \frac{\displaystyle \sum_{k=1}^N w_k\,\bigl(d_{k,i} - d_{k,j}\bigr)^2}{a^2 \left(S - \dfrac{Q}{S}\right)}.
     $$
   
3. **Non–Weighted Version:**
   - **Simple Means:**
     $$
     \mu_i = \frac{1}{N}\sum_{k=1}^N X_{k,i},\quad \mu_j = \frac{1}{N}\sum_{k=1}^N X_{k,j},
     $$
     $$
     m_i = \frac{1}{N}\sum_{k=1}^N X^{\text{full}}_{k,i},\quad m_j = \frac{1}{N}\sum_{k=1}^N X^{\text{full}}_{k,j}.
     $$
   - **Centering and Scaling:**
     $$
     d_{k,i} = \frac{X_{k,i} - \mu_i}{m_i},\quad d_{k,j} = \frac{X_{k,j} - \mu_j}{m_j}.
     $$
   - **lrv Computation:**
     $$
     \operatorname{lrv}_{ij} = \frac{1}{a^2 (N-1)} \sum_{k=1}^N \bigl(d_{k,i} - d_{k,j}\bigr)^2.
     $$

---

#### **Case 2: $a$ is NA (No Transformation)**

1. **For Each Observation $k$:**
   $$
   v_k = \log\!\left(\frac{Y_{k,i}}{Y_{k,j}}\right).
   $$
   
2. **Weighted Version:**
   - **Weights:**
     $$
     w_k = W_{k,i}\,W_{k,j}.
     $$
   - **Weighted Mean:**
     $$
     \mu = \frac{\sum_{k=1}^N w_k\, v_k}{\sum_{k=1}^N w_k}.
     $$
   - **Variance (lrv):**
     $$
     \text{Numerator} = \sum_{k=1}^N w_k\,\bigl(v_k - \mu\bigr)^2,
     $$
     with
     $$
     S = \sum_{k=1}^N w_k,\quad Q = \sum_{k=1}^N w_k^2,
     $$
     so that
     $$
     \operatorname{lrv}_{ij} = \frac{\displaystyle \sum_{k=1}^N w_k\,\bigl(v_k - \mu\bigr)^2}{S - \dfrac{Q}{S}}.
     $$
   
3. **Non–Weighted Version:**
   - **Simple Mean:**
     $$
     \mu = \frac{1}{N}\sum_{k=1}^N v_k.
     $$
   - **Variance (lrv):**
     $$
     \operatorname{lrv}_{ij} = \frac{1}{N-1}\sum_{k=1}^N \bigl(v_k - \mu\bigr)^2.
     $$

---

### **Summary**

The code calculates a log–ratio variance (lrv) statistic for each pair $(i,j)$ by performing the following steps:

1. **If $a$ is provided:**  
   - Transform the data via $X = Y^a$ (and similarly for the full data).
   - Center and scale $X$ using (weighted or unweighted) means and full–data means.
   - Compute a (weighted) sum of squared differences normalized by $a^2$ and an appropriate degrees–of–freedom correction.

2. **If $a$ is not provided:**  
   - Compute the log–ratio $v_k = \log(Y_{k,i}/Y_{k,j})$.
   - Then compute its (weighted or unweighted) variance, again with a degrees–of–freedom correction.

This pseudocode with equations should help clarify the mathematical steps behind the implementation.

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzU0MTI2NTQ5XX0=
-->