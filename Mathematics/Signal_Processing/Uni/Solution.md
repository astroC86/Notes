#### Hand-Written Solution
The Complex exponential equation is: 
$\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;f(t) = \sum_{n=-\infty}^{\infty} F_n e^{j\omega_o nt}$
where:
$F_n =\frac{1}{T_o}\int_{0}^{T_o} f(t) e^{-j\omega_o nt} dt$

$F_0 =\frac{1}{T_o}\int_{0}^{T_o} f(t) dt$

Solution:
$f(t)  = e^{-t}\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\; \text{where  0 }< t < \pi$
$\omega_o = \frac{2\pi}{\pi}= 2$

Finding $F_n$:

$$\begin{align*}
F_n &=\frac{1}{\pi}\int_{0}^{\pi} e^{-t} e^{-2jnt} dt\\
&=\frac{1}{\pi}\int_{0}^{\pi} e^{-(1+2jn)t} dt\\
&= \frac{1}{\pi}\frac{1}{-1-2nj} \times \frac{-1+2nj}{-1+2nj}\left[e^{-(1+2jn)t} \right]_0^{\pi}\\
&= \frac{1}{\pi}\frac{1}{-1-2nj} \times \frac{-1+2nj}{-1+2nj}\left[[]_{\pi}-[]_{0}\right]\\
&= \frac{1}{\pi}\frac{-1+2nj}{-1+4n^{2}}[[]_{\pi}-[]_{0}]\end{align*}$$

Solving $[]_0$ :

$e^{-(1+2jn)0} = e^{0} = 1$

Solving $[]_{\pi}$

$e^{-(1+2jn)\pi}$

Expanding the exponent:
$e^{-\pi}e^{-2jn\pi}$

Following the relation:

$e^{\pm j\omega_ot} = cos(\omega_ot) \pm jsin(\omega_ot)$

$[]_{\pi}$  becomes:

$e^{-\pi} e^{-2jn\pi} =e^{-\pi}[cos(2\pi n) - jsin(2\pi n)]$

Combining the solutions:
$= \frac{1}{\pi}\frac{-1+2nj}{-1+4n^{2}}[e^{-\pi}[cos(2\pi n) - jsin(2\pi n)] -1]$

Multiplying $\frac{1}{\pi}\frac{-1+2nj}{-1+4n^{2}}$ into the brackets we get:

$F_n= \dfrac{e^{-{\pi}}((2n+j)sin(2\pi n)+(2jn-1)cos(2\pi n)-2e^{\pi}jn+e^{\pi})}{4\pi n^2+\pi}$

Finding $F_0$ :

$F_0 =\frac{1}{T_o}\int_{0}^{T_o} f(t) dt$

$=\frac{1}{\pi}\int_{0}^{\pi} e^{-t}dt$

$=\frac{1}{\pi}[\dfrac{e^{-t}}{-1}]_{0}^{\pi}$

Flipping the integral and solving:

$F_0=\frac{1}{\pi}[\dfrac{e^{-t}}{-1}]_{\pi}^{0} = \frac{1}{\pi}[1-e^{\pi}] = \dfrac{1-e^{\pi}}{\pi}$


We will be evaluating:
$\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;f(t) = \sum_{n=0}^{\infty} F_n e^{j\omega_o nt}$

$F_1 \;=\frac{e^{\pi}-2 e^{\pi} j+2 j-1}{5 \pi e^{\pi}} \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\; F_2 \;= \frac{e^{\pi}-4 e^{\pi} j+4 j-1}{17 \pi e^{\pi}}$

$F_3 \;= \frac{e^{\pi}-6 e^{\pi} j+6 j-1}{37 \pi e^{\pi}} \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\; F_4 \;=\frac{e^{\pi}-8 e^{\pi} j+8 j-1}{65 \pi e^{\pi}}$

$F_5 \;=\frac{e^{\pi}-10 e^{\pi} j+10 j-1}{101 \pi e^{\pi}} \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\; F_6 \;=\frac{e^{\pi}-12 e^{\pi} j+12 j-1}{145 \pi e^{\pi}}$

$F_7 \;=\frac{e^{\pi}-14 e^{\pi} j+14 j-1}{197 \pi e^{\pi}} \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;F_8 \; =\frac{e^{\pi}-16 e^{\pi} j+16 j-1}{257 \pi e^{\pi}}$

$F_9 \;=\frac{e^{\pi}-18 e^{\pi} j+18 j-1}{325 \pi e^{\pi}} \;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;\;F_{10} =\frac{e^{\pi}-20 e^{\pi} j+20 j-1}{401 \pi e^{\pi}}$


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NzU0NTg1NDldfQ==
-->