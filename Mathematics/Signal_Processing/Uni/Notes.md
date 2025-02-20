## Useful Signals
### Properties of Dirac Delta
```mermaid
graph LR;
style A fill:#0000;
style B fill:#0000;
style C fill:#0000;
A[Dirac Delta] -- Integration--> B[Unit Step]
B --derivative--> A
B --Integration--> C[Ramp]
C --derivative-->B
```
## Signal Transforms
Operations applied on a signal and precedence 
- Shift
- Scale
## Signal Classifications
- Time variant, Or Time Invariant
	- **TV**  :  Time Scaling or  $f(t)x(t)$ 
	- **TIV** : Otherwise
- Causal, Non-Causal
	- **C**  : $x(t)$ or $x(t- \dots)$
	- **NC**: time scaling or $x(t+\dots)$
- Instantaneous, Dynamic
	- **I**   : $x(t)$ only
	- **D** : $x(t\pm\dots)$, time scaling, derivative of $y$, integral of $x$
- Linear, Non-Linear
	- **L**    : Otherwise
	- **NL** :
		- <img src="https://latex.codecogs.com/png.latex?\left.\left.\begin{matrix}&space;cos\\&space;sin\\&space;ln\\&space;log&space;\end{matrix}\right\(&space;x(t)\,or\,y(t)&space;\right\)" title="\left.\left.\begin{matrix} cos\\ sin\\ ln\\ log \end{matrix}\right\( x(t)\,or\,y(t) \right\)" /> 
		- $\;y^k(t) / x^k(t)$
		- $\;x(t)x(t\pm a)/y(t)y(t\pm a)$
		- $x(t)\pm a/f(t)$
- Stable, Unstable
	- **NS**    :
		- Hide x,y and check if there are growing terms
			- $t^k\quad t\in \mathbb{R}^+$
			- $e^{at}\quad a >1$
		- Compare the order of x and y denoted as M,N respectively:
			- $M > N$
	- **S** : Otherwise
- Invertible, Non-Invertible
	- **IV**    : odd power
	- **NIV**:  even power or contains differentiation
## Impulse Response
$$h(t) = [P(D)y_n(t)]u(t)$$
## Energy, Power,RMS,and Mean DC of a function
### Power
Periodic: 
$$\frac{1}{T}\int_{<T>} |x(t)|^2dt$$

- Special case
		- Sinusoidal: $\frac{A^2}{2}$
 
Non-Periodic:
$$\lim_{T\rightarrow \infty}\frac{1}{2T}\int_{-T}^{T} |x(t)|^2dt$$
### RMS
$$RMS = \sqrt{P_{avg}}$$
### Energy
Periodic  : $E_{total}= \;\infty$
 Non-Periodic:
$$\int_{-\infty}^{\infty}|x(t)|^2dt$$
### Mean DC value
$$DC = \lim_{T\rightarrow\infty}\frac{1}{T}\int_{-T/2}^{T/2}x(t)dt$$
## Fourier Series 
### The Compact Fourier Series
The compact Fourier Series is described as follows: 
$$x(t)=C_{0}+\sum_{n=1}^{\infty} C_{n} \cos \left(n \omega_{0} t+\theta_{n}\right)$$
Where:
$C_{0}=a_{0}$
$C_{n}=\sqrt{a_{n}^{2}+b_{n}^{2}} \quad$ Amplitude of $\mathrm{n}^{\text {th }}$ harmonic
$\theta_{n}=\tan ^{-1}\left(\frac{-b_{n}}{a_{n}}\right)$ Phase of $n^{\text {th }}$ harmonic

### Complex Fourier Series
The complex Fourier Series is defined as follows:
$$x(t)=\sum_{n=-\infty}^{\infty} D_{n} e^{j n \omega_{0} t}$$
Where
$$D_{n}=\frac{1}{T_{0}} \int_{T_{0}} x(t) e^{-j n \omega_{0} t} d t$$
$D_{n}$ is generally complex


For general $\mathrm{x}(\mathrm{t})$, relation to trigonometric series coefficient is:
$$\mathrm{D}_{0}=\mathrm{a}_{0} \quad \text { for } n=0$$

$D_{n}=\frac{1}{2}\left(a_{n}-j b_{n}\right)$ for positive value of $n$
$D_{-n}=\frac{1}{2}\left(a_{n}+j b_{n}\right)$ for negative value of $n$

**Note**: When $\mathrm{x}(\mathrm{t})$ is real, $\mathrm{a}_{\mathrm{n}}$ and $\mathrm{b}_{\mathrm{n}}$ are real, and $\mathrm{D}_{\mathrm{n}}$ and $\mathrm{D}_{-\mathrm{n}}$ are conjugates.

$$
D_{-n}=D_{n}{ }^{*}
$$

$$\begin{array}{c}
\left|D_{n}\right|=\left|D_{-n}\right|=\frac{1}{2} C_{n} \quad n \neq 0 \\
\angle D_{n}=\theta_{n} \quad \text { and } \quad \angle D_{-n}=-\theta_{n} \\
D_{n}=\left|D_{n}\right| e^{j \theta_{n}} \quad \text { and } \quad D_{-n}=\left|D_{n}\right| e^{-j \theta_{n}}
\end{array}
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1ODAwMTE5OV19
-->