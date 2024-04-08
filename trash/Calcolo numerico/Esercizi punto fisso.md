$f(x)=\sqrt{x}-\frac{1}{2\sqrt{1-x}}$
$f'(x)=\frac{1}{2\sqrt{x}}-\frac{1}{4(1-x)^\frac{3}{2}}$
$f''(x)=-\frac{1}{4}x^{-\frac{3}{2}}-\frac{3}{8}(1-x)^{-\frac{5}{2}}$

$g(x)=\frac{1}{4(1-x)}$
$g'(x)=\frac{1}{4(1-x)^2}$ è $<1$ solo se $x<\frac{1}{2}$


$g(x)=\frac{1}{2}(x+\frac{α}{x})$ con $α>0$
$g'(x)=\frac{1}{2}-\frac{α}{2x^{2}}$
$|1-αx^{-2}|<2$
- Se $1-αx^{-2}≥0$, cioè $x^2≥α$ (cioè $x≤-\sqrt{a}∨x≥\sqrt{a}$):
$1-αx^{-2}<2$
$-αx^{-2}<1$ (sempre vero)
- Se $1-αx^{-2}<0$, cioè $x^2<α$ (cioè $\sqrt{a}<x<\sqrt{a}$):
$αx^{-2}-1<2$
$x^2>\frac{1}{3}α$ (cioè $x≤-\frac{1}{3}\sqrt{a}∨x≥\frac{1}{3}\sqrt{a}$)

Combinando tutto, la funzione converge se $x≤-\frac{1}{3}\sqrt{a}∨x≥\frac{1}{3}\sqrt{a}$


$f(x)=(x-1)e^{x+1}-a$
$f'(x)=e^{x+1}x+e^{x+1}-e^{x+1}=e^{x+1}x$
$g(x)=x-\frac{(x-1)e^{x+1}-a}{e^{x+1}x}=x-1+\frac{1}{x}+\frac{a}{e^{x+1}x}$
$g'(x)=1-\frac{1}{x^2}+a(-e^{-x-1}x^{-1}-e^{-x-1}x^{-2})=1-\frac{1}{x^2}-\frac{a(x+1)}{e^{x+1}x^2}$

### Simulazione prima prova

$f(x)=\cos(x)-x+3$

1. Intervallo di separazione $f(x)=0$
Il coseno ha un valore da $-1$ a $1$.
Se avessimo $f(x)=-x+3$ (radice a $3$), si dista di questa quantità da $2$ a $4$.
Si può informalmente dedurre che da $2$ a $3$, dato che il coseno è negativo (e smette di esserlo poco dopo), la radice dovrà essere lì.
Intervallo: $(2,3)$.

2. Studio metodo tangenti
$f'(x)=-\sin(x)-1$
$f''(x)=-\cos(x)$
$g(x)=x-\frac{f(x)}{f'(x)}=x+\frac{\cos(x)-x+3}{\sin(x)+1}$
$g'(x)=-\cos(x)\frac{\cos(x)-x+3}{(\sin(x)+1)^2}$

$|-\cos(x)\frac{\cos(x)-x+3}{(\sin(x)+1)^2}|<|\frac{\cos(x)-x+3}{(\sin(x)+1)^2}|$
Il seno è $>0$ nell'intervallo, quindi:
$|\frac{\cos(x)-x+3}{(\sin(x)+1)^2}|<|\cos(x)-x+3|$

Nell'intervallo, il coseno $<0$:
$|\cos(x)-x+3|<|-x+3|$

Che nell'intervallo è $<1$.

Ordine:

$g'(α)=-\cos(α)\frac{\cos(α)-α+3}{(\sin(α)+1)^2}=-\cos(α)\frac{f(α)}{(\sin(α)+1)^2}=0$
Quindi la convergenza è almeno quadratica.

3. Convergenza $g(x)=\frac{4}{3}x-\frac{1}{3}\cos(x)-1$
$g'(x)=\frac{4}{3}+\frac{1}{3}\sin(x)$
Il cui valore assoluto non è mai $<1$, quindi non converge.
