# 1. Problem Definition

We need to compute the Long-Run Variance (LRV) for transformed variables under weighted conditions. Given:

* Transformed variables:
  $X_{k,i} = Y_{k,i}$, $X_{k,i}^{\text{full}} = (Y_{k,i}^{\text{full}})^n$

* Weights:
  $w_k = W_k$, $w_k^{\text{full}} = W_k^{\text{full}}W_{k,i}^{\text{full}}$

* Centering and scaling:
  $d_{k,i} = \frac{X_{k,i} - \mu_i}{m_i}$, $d_{k,j} = \frac{X_{k,j} - \mu_j}{m_j}$

* LRV formula:
  $\text{lrv}_d = \frac{\sum_{k=1}^N w_k(d_{k,i} - d_{k,j})^2}{a^2(S - \frac{Q}{S})}$ where $S = \sum w_k$, $Q = \sum w_k^2$

# 2. Expand the Numerator

The numerator is the weighted sum of squared differences:

$\text{Numerator} = \sum_{k=1}^N w_k(d_{k,i} - d_{k,j})^2$

Expand the squared term:

$\text{Numerator} = \sum_{k=1}^N w_k(d_{k,i}^2 - 2d_{k,i}d_{k,j} + d_{k,j}^2)$

$= \sum_{k=1}^N w_kd_{k,i}^2 - \sum_{k=1}^N 2w_kd_{k,i}d_{k,j} + \sum_{k=1}^N w_kd_{k,j}^2$

# 3. Substitute Scaled Variables

Using the definitions of $d_{k,i}$ and $d_{k,j}$:

$\text{Term 1} = \sum_{k=1}^N w_k\left(\frac{X_{k,i} - \mu_i}{m_i}\right)^2 = \frac{1}{m_i^2}\sum_{k=1}^N w_k(X_{k,i} - \mu_i)^2$

$\text{Term 3} = \sum_{k=1}^N w_k\left(\frac{X_{k,j} - \mu_j}{m_j}\right)^2 = \frac{1}{m_j^2}\sum_{k=1}^N w_k(X_{k,j} - \mu_j)^2$

$\text{Term 2} = \sum_{k=1}^N w_k\frac{(X_{k,i} - \mu_i)(X_{k,j} - \mu_j)}{m_im_j} = \frac{1}{m_im_j}\sum_{k=1}^N w_k(X_{k,i} - \mu_i)(X_{k,j} - \mu_j)$

# 4. Compute Weighted Means

The weighted means $\mu_i,\mu_j,m_i,m_j$ are defined as:

$\mu_i = \frac{\sum_{k=1}^N w_kX_{k,i}}{S}$, $\mu_j = \frac{\sum_{k=1}^N w_kX_{k,j}}{S}$

$m_i = \frac{\sum_{k=1}^N w_k^{\text{full}}X_{k,i}^{\text{full}}}{\sum w_k^{\text{full}}}$, $m_j = \frac{\sum_{k=1}^N w_k^{\text{full}}X_{k,j}^{\text{full}}}{\sum w_k^{\text{full}}}$

# 4a. Weighted Variance Identity

Before proceeding with simplification, we prove the key identity for weighted variance:

$\sum_{k=1}^N w_k(X_k - \mu)^2 = \sum_{k=1}^N w_kX_k^2 - \frac{(\sum w_kX_k)^2}{S}$

where $S = \sum w_k$ and $\mu = \frac{\sum w_kX_k}{S}$

Proof:

1. Expand the square:
   $\sum_{k=1}^N w_k(X_k - \mu)^2 = \sum_{k=1}^N w_k(X_k^2 - 2X_k\mu + \mu^2)$

2. Distribute weights:
   $= \sum_{k=1}^N w_kX_k^2 - 2\mu\sum_{k=1}^N w_kX_k + \mu^2\sum_{k=1}^N w_k$

3. Substitute $\mu = \frac{\sum w_kX_k}{S}$ and $\sum w_k = S$:
   $= \sum_{k=1}^N w_kX_k^2 - 2\frac{(\sum w_kX_k)^2}{S} + \frac{(\sum w_kX_k)^2}{S}$

4. Combine terms:
   $= \sum_{k=1}^N w_kX_k^2 - \frac{(\sum w_kX_k)^2}{S}$

# 4b. Weighted Covariance Identity

We also need the weighted covariance identity:

$\sum_{k=1}^N w_k(X_k - \mu_X)(Y_k - \mu_Y) = \sum_{k=1}^N w_kX_kY_k - \frac{(\sum w_kX_k)(\sum w_kY_k)}{S}$

Proof:

1. Expand product:
   $\sum_{k=1}^N w_k(X_k - \mu_X)(Y_k - \mu_Y) = \sum_{k=1}^N w_k(X_kY_k - X_k\mu_Y - Y_k\mu_X + \mu_X\mu_Y)$

2. Distribute summation:
   $= \sum_{k=1}^N w_kX_kY_k - \mu_Y\sum_{k=1}^N w_kX_k - \mu_X\sum_{k=1}^N w_kY_k + \mu_X\mu_Y\sum_{k=1}^N w_k$

3. Substitute weighted means:
   $= \sum_{k=1}^N w_kX_kY_k - \frac{\sum w_kY_k}{S}\sum_{k=1}^N w_kX_k - \frac{\sum w_kX_k}{S}\sum_{k=1}^N w_kY_k + \frac{\sum w_kX_k}{S}\frac{\sum w_kY_k}{S}S$

4. Simplify:
   $= \sum_{k=1}^N w_kX_kY_k - \frac{(\sum w_kX_k)(\sum w_kY_k)}{S}$

# 5. Simplify Term 1 and Term 3

Using the weighted variance identity proven in Section 4a:

$\sum_{k=1}^N w_k(X_{k,i} - \mu_i)^2 = \sum_{k=1}^N w_kX_{k,i}^2 - \frac{(\sum w_kX_{k,i})^2}{S}$

Thus:

$\text{Term 1} = \frac{1}{m_i^2}\left(\sum w_kX_{k,i}^2 - \frac{(\sum w_kX_{k,i})^2}{S}\right)$

$\text{Term 3} = \frac{1}{m_j^2}\left(\sum w_kX_{k,j}^2 - \frac{(\sum w_kX_{k,j})^2}{S}\right)$

# 6. Simplify Term 2 (Covariance Term)

Using the weighted covariance identity proven in Section 4b:

$\sum_{k=1}^N w_k(X_{k,i} - \mu_i)(X_{k,j} - \mu_j) = \sum_{k=1}^N w_kX_{k,i}X_{k,j} - \frac{(\sum w_kX_{k,i})(\sum w_kX_{k,j})}{S}$

Thus:

$\text{Term 2} = \frac{1}{m_im_j}\left(\sum w_kX_{k,i}X_{k,j} - \frac{(\sum w_kX_{k,i})(\sum w_kX_{k,j})}{S}\right)$

# 7. Combine All Terms

The numerator becomes:

$\text{Numerator} = \frac{1}{m_i^2}\left(\sum w_kX_{k,i}^2 - \frac{(\sum w_kX_{k,i})^2}{S}\right)$
$+ \frac{1}{m_j^2}\left(\sum w_kX_{k,j}^2 - \frac{(\sum w_kX_{k,j})^2}{S}\right)$
$- \frac{2}{m_im_j}\left(\sum w_kX_{k,i}X_{k,j} - \frac{(\sum w_kX_{k,i})(\sum w_kX_{k,j})}{S}\right)$

# 8. Denominator Derivation

The denominator adjusts for weighting effects using Bessel's correction for weighted data:

$\text{Denominator} = a^2\left(S - \frac{Q}{S}\right)$, where $Q = \sum w_k^2$

* Intuition:
  * $S - \frac{Q}{S}$ approximates the effective sample size for weighted data
  * For unweighted data $(w_k = 1)$, $S = N$, $Q = N$, and $S - \frac{Q}{S} = N - 1$, matching the original formula

# 9. Final LRV Formula

$\text{lrv}_d = \frac{\text{Numerator}}{\text{Denominator}} = \frac{\text{Sum of weighted scaled terms}}{a^2\left(S - \frac{Q}{S}\right)}$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTA2NzA2MjBdfQ==
-->