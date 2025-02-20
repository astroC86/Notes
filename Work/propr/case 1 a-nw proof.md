### Mathematical Derivation of the Online LRV Algorithm

**Given Definitions:**
1. **Means:**
   - $\mu_i = \frac{1}{N}\sum_{k=1}^N X_{k,i}$, $\mu_j = \frac{1}{N}\sum_{k=1}^N X_{k,j}$  
   - $m_i = \frac{1}{N}\sum_{k=1}^N X^{\text{full}}_{k,i}$, $m_j = \frac{1}{N}\sum_{k=1}^N X^{\text{full}}_{k,j}$

2. **Centered and Scaled Data:**
   - $d_{k,i} = \frac{X_{k,i} - \mu_i}{m_i}$, $d_{k,j} = \frac{X_{k,j} - \mu_j}{m_j}$

3. **LRV Formula:**
   $$
   \operatorname{lrv}_{ij} = \frac{1}{a^2 (N-1)} \sum_{k=1}^N \bigl(d_{k,i} - d_{k,j}\bigr)^2
   $$

---

#### **Step 1: Expand the Squared Term**
Expand $(d_{k,i} - d_{k,j})^2$:
$$
\bigl(d_{k,i} - d_{k,j}\bigr)^2 = d_{k,i}^2 + d_{k,j}^2 - 2 d_{k,i} d_{k,j}
$$

Substitute $d_{k,i} = \frac{X_{k,i} - \mu_i}{m_i}$ and $d_{k,j} = \frac{X_{k,j} - \mu_j}{m_j}$:
$$
\begin{aligned}
\sum_{k=1}^N \bigl(d_{k,i} - d_{k,j}\bigr)^2 &= \sum_{k=1}^N \left[\frac{(X_{k,i} - \mu_i)^2}{m_i^2} + \frac{(X_{k,j} - \mu_j)^2}{m_j^2} - 2 \frac{(X_{k,i} - \mu_i)(X_{k,j} - \mu_j)}{m_i m_j}\right] \\
&= \frac{1}{m_i^2} \sum_{k=1}^N (X_{k,i} - \mu_i)^2 + \frac{1}{m_j^2} \sum_{k=1}^N (X_{k,j} - \mu_j)^2 \\
&\quad - \frac{2}{m_i m_j} \sum_{k=1}^N (X_{k,i} - \mu_i)(X_{k,j} - \mu_j).
\end{aligned}
$$

---

#### **Step 2: Relate Sums to Variances and Covariance**
The terms can be expressed using:
1. **Variance of $X_i$:**
   $$
   \operatorname{Var}(X_i) = \frac{1}{N-1} \sum_{k=1}^N (X_{k,i} - \mu_i)^2
   $$
2. **Variance of $X_j$:**
   $$
   \operatorname{Var}(X_j) = \frac{1}{N-1} \sum_{k=1}^N (X_{k,j} - \mu_j)^2
   $$
3. **Covariance of $X_i$ and $X_j$:**
   $$
   \operatorname{Cov}(X_i, X_j) = \frac{1}{N-1} \sum_{k=1}^N (X_{k,i} - \mu_i)(X_{k,j} - \mu_j)
   $$

Substitute these into the LRV formula:
$$
\begin{aligned}
\operatorname{lrv}_{ij} &= \frac{1}{a^2 (N-1)} \left[
\frac{(N-1) \operatorname{Var}(X_i)}{m_i^2} + \frac{(N-1) \operatorname{Var}(X_j)}{m_j^2} - \frac{2 (N-1) \operatorname{Cov}(X_i, X_j)}{m_i m_j}
\right] \\
&= \frac{1}{a^2} \left[
\frac{\operatorname{Var}(X_i)}{m_i^2} + \frac{\operatorname{Var}(X_j)}{m_j^2} - \frac{2 \operatorname{Cov}(X_i, X_j)}{m_i m_j}
\right].
\end{aligned}
$$

---

#### **Step 3: Compute Statistics Incrementally**
We compute the following quantities **online** (i.e., one-pass):
1. **Means $\mu_i$, $\mu_j$, $m_i$, $m_j$**  
   Using Welford’s algorithm:
   $$
   \mu_n = \mu_{n-1} + \frac{x_n - \mu_{n-1}}{n}
   $$

2. **Sum of Squares for Variance**  
   For $\operatorname{Var}(X_i)$, compute:
   $$
   \text{sum\_sq}_i = \sum_{k=1}^N X_{k,i}^2 - N \mu_i^2
   $$

3. **Covariance**  
   Track the co-moment $C = \sum_{k=1}^N (X_{k,i} - \mu_i)(X_{k,j} - \mu_j)$ using:
   $$
   C_n = C_{n-1} + (x_n - \mu_{n-1})(y_n - \mu_{n})
   $$

---

#### **Step 4: Final LRV Calculation**
After processing all $N$ data points:
1. Compute scaled terms:
   - $\frac{\operatorname{Var}(X_i)}{m_i^2} = \frac{\text{sum\_sq}_i}{(N-1) m_i^2}$
   - $\frac{\operatorname{Var}(X_j)}{m_j^2} = \frac{\text{sum\_sq}_j}{(N-1) m_j^2}$
   - $\frac{\operatorname{Cov}(X_i, X_j)}{m_i m_j} = \frac{C}{(N-1) m_i m_j}$

2. Combine terms:
   $$
   S = \text{sum\_sq}_i \cdot \frac{1}{m_i^2} + \text{sum\_sq}_j \cdot \frac{1}{m_j^2} - 2 \cdot \frac{C}{m_i m_j}
   $$

3. Divide by $a^2 (N-1)$:
   $$
   \operatorname{lrv}_{ij} = \frac{S}{a^2 (N-1)}
   $$

---

### Summary of Key Equations
1. **Incremental Mean Updates**:
   $$
   \mu_{i,n} = \mu_{i,n-1} + \frac{X_{i,n} - \mu_{i,n-1}}{n}
   $$

2. **Covariance Update**:
   $$
   C_n = C_{n-1} + (X_{i,n} - \mu_{i,n-1})(X_{j,n} - \mu_{j,n})
   $$

3. **Final LRV**:
   $$
   \operatorname{lrv}_{ij} = \frac{1}{a^2 (N-1)} \left[
   \frac{\text{sum\_sq}_i}{m_i^2} + \frac{\text{sum\_sq}_j}{m_j^2} - \frac{2C}{m_i m_j}
   \right]
   $$

This derivation matches the provided Python code, which incrementally computes $\mu_i$, $\mu_j$, $m_i$, $m_j$, $C$, and $\text{sum\_sq}_i$, $\text{sum\_sq}_j$, then combines them into the LRV formula.
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDc4MDUzNzQwXX0=
-->