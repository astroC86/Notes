## Mapping of the Z domain 
Recall that 
$s=\sigma+j\omega$

**Lemma**: the Z transform is the Equivalent in Discrete form of the Continuous time Laplace transform

$F(s) = \mathcal{L}\{f(t)\}$

$F(s) = \int_{-\infty}^{\infty} f(t)e^{-st}dt$

After Sampling:

$t \rightarrow nT \text{ and } f(t) \rightarrow f(n)$

$F(\mathcal{z}) = \sum_{n=-\infty}^{\infty} f(n)\mathcal{e}^{-snT}$

$\quad\quad\quad\text{where }\mathcal{z} = e^{sT} \\ \,F(\mathcal{z}) = \sum_{n=-\infty}^{\infty} f(n)\mathcal{z}^{-n}\quad \therefore\text{General Form of the Z transform}$

The Summation must converge for a solution to **exist**, which is defined by the **Region of convergence (ROC)**.


#### Mapping between the S-plane and the Z-plane 
Laplace Transform is 
Given that:
$$\begin{align*}
\mathcal{z} &= e^{sT} &\text{ since } s=\sigma+j\omega\\
&= e^{(\sigma+j\omega)T}\\
&= e^{\sigma T}e^{j\omega T}     &\text{ since }e^{j\square } = cos(\square ) +j sin(\square)\\
&= e^{\sigma T}[cos(\omega T)+jsin(\omega T)]\\
\therefore& =  e^{\sigma T}cos(\omega T)+je^{\sigma T}sin(\omega T)\\
\therefore&=u +jv \\
&\text{ where }\\
&\quad\quad u = \mathcal{Re}\{\mathcal{z}\} =  e^{\sigma T}cos(\omega T) \\
&\quad\quad v = \mathcal{Im}\{\mathcal{z}\}=e^{\sigma T}sin(\omega T)\\\,\\
&\quad\quad \sigma  = \mathcal{Re}\{\mathcal{s}\} \\
&\quad\quad \omega= \mathcal{Im}\{\mathcal{s}\}
\end{align*}
$$


Mapping in the S domain:
$$
\begin{align*}
\text{LHP at}  \,&\sigma < 0\\
\text{RHP at}\,&\sigma > 0\\
j\omega\;\text{ axis at }\,&\sigma = 0
\end{align*}
$$

Mapping in the Z domain:

Case 1: $j\omega\;\text{ axis }\,\sigma = 0$
$\therefore u^2+v^2=1, \text{which is a circle of radius 1}$

Case 2: $\sigma >0, \text{RHP}$
$u^2+v^2=e^{2\sigma T}, \text{when }\sigma >> \text{ circle radius is greater than 1 i.e region outside the 1}$

Case 3: $\sigma <0, \text{LHP}$
$u^2+v^2=e^{2\sigma T}, \text{when }\sigma << \text{ circle radius is less than 1 i.e region inside the 1}$

####  How to solve mapping problems:
**Problem Type 1:**
Given point in the $\mathcal{Z}$ domain find its equivalent in the $\mathcal{S}$ domain:
$z =\bigcirc +j\triangle$
$u = \bigcirc$
$v = \triangle$
1 ) Get the $\omega$
$\omega = tan^{-1}(\dfrac{v}{u})$
2 ) get $\sigma$ 
substitute $u=e^{\sigma T}cos(\omega T)$ 

**Problem Type 2:**
Given point in the $\mathcal{S}$ domain find its equivalent in the $\mathcal{Z}$ domain:
$s = \square +j\blacktriangle$
$\sigma = \square$
$\omega = \blacktriangle$
$u = e^{\sigma T}cos(\omega T)$
$v=e^{\sigma T}sin(\omega T)$
$\therefore z = u+jv$




## Z transform of Elementary Functions
| $f(n)$ |$F(\mathcal{z})$  | ROC|
|--|--|--|
| $\delta (n)$| 1 |$\forall z$|
|$\mu(n)$ |$\frac{1}{1-z^{-1}}$|\|z\|>1|
| $a^n \mu(n)$|$\frac{1}{1-z^{-1}a}$|\|z\|>\|a\||
|$na^{n}\mu (n)$|$\dfrac{az^{-1}}{(1-az^{-1})^2}$|\|z\|>\|a\||
| $e^{-n\sigma} \mu(n)$|$\frac{1}{1-e^{-\sigma}z^{-1}}$ |\|z\|>$e^{-\sigma}$|
|$\bigcirc^{n\square}\mu(n)$|$\frac{1}{1-\bigcirc^\square z^{-1}}$|\|z\|> $\bigcirc^\square$|
|$-a^n \mu(-n -1)$|$\dfrac{1}{1-az^{-1}}$| \|z\|<\|a\| |
|$-a^n \mu(-n -1)$|$\dfrac{az^{-1}}{(1-az^{-1})^2}$| \|z\|<\|a\| |


### LTI Representation
**1 )** Convolution
$y(n) = x(n) * h(n)$ 
$Y(z) = H(z)\cdot X(z)$
$H(z)=\mathcal{Z}\{h(n)\}=\frac{Y(z) }{X(z)}$
**2 )** Difference Equation Representation
$y(n) = -\sum_{k=1}^{N}a_k y(n-k) + \sum_{k=1}^{M}b_k x(n-k)$
$H(z) =\dfrac{\sum_{k=1}^{M}b_k z^{-k}}{1+\sum_{k=1}^{N}a_k z^{-k}}$

**3 )** Transfer Function Using Poles and Zeros
$H(z) = k \cdot \dfrac{\Pi_{k=1}^{M}(z-z_{k})}{\Pi_{k=1}^{N} (z-p_k)}$

where $k$ is the gain
* the gain, poles and zeros could be given and the equation to be derived.

**4 )** Block diagram and derive the difference equation then the $H(z)$

### Stability in the Z-Domain
Conditions for stability: 
- No repeated poles lie on the unit circle but one lie on the unit circle
- All other poles Inside the unit circle 

### Fourier Representation of discrete time signals
|Time Domain|Frequency Domain|	Tool|
|------------|---------------|---------------|
|Discrete    |Periodic       |Discrete form|
|Continuous  |Non-Periodic   |Continuous form |
|Periodic    |Discrete       |Fourier Series|
|Non-Periodic|Continuous     |Fourier Transform|

1 ) Discrete , Periodic (N)   DTFS-> Discrete, Periodic (N)
2 ) Discrete ,Non-periodic  DTFT-> Continuous, Periodic (2pi)

 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3ODQwMzU1MDNdfQ==
-->