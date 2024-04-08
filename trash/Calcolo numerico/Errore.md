Errore totale:
- $ϵ_{tot}=ϵ_{alg}+ϵ_{in}$
- $ϵ_{tot}=\frac{ψ(\tilde{x})-f(x)}{f(x)}$

### Errore inerente
$ϵ_{in}≐c_xϵ_x$

- Errore relativo: $ϵ_x=\frac{\tilde{x}-x}{x}$
- Coefficiente di amplificazione: $c_x=\frac{xf'(x)}{f(x)}$
 
 Per funzioni con più parametri:
- $ϵ_{in}≐∑\limits_ic_iϵ_i$
- $c_i=\frac{x_i}{f(x)}\frac{δf(x)}{δx_i}$

Esempi:
- $f(x_1,x_2)=x_1+x_2$
	- $c_1=\frac{x_1}{x_1+x_2}$
	- $c_2=\frac{x_2}{x_1+x_2}$
	- Nota: se i parametri sono dello stesso segno, il coefficiente è al massimo 1. Se sono di segno opposto, non c'è limite.
- $f(x_1,x_2)=x_1-x_2$
	- $c_1=\frac{x_1}{x_1-x_2}$
	- $c_2=\frac{x_2}{x_2-x_1}$
- $f(x_1,x_2)=x_1x_2$
	- $c_1=1$
	- $c_2=1$
- $f(x_1,x_2)=\frac{x_1}{x_2}$
	- $c_1=1$
	- $c_2=-1$

#### Esempio sottrazione

In un sistema con 5 cifre decimali, calcoliamo l'errore di $0.123456-0.123454$.
Normalmente farebbe $2·10^{-6}$.

- $x_1=0.123456 \quad \tilde{x}_1=0.12346$
	- $ϵ_1=\frac{0.12346-0.123456}{0.123456}=\frac{4·10^{-6}}{0.123456}$
- $x_2=0.123454 \quad \tilde{x}_1=0.12345$
	- $ϵ_2=\frac{0.12345-0.123454}{0.123454}=-\frac{4·10^{-6}}{0.123454}$

Con le $x$ arrotondate, la sottrazione fa $1·10^{-5}$.
$ϵ_{in}=\frac{1·10^{-5}-2·10^{-6}}{2·10^{-6}}=4$

- $c_1=\frac{0.123456}{0.123456-0.123454}=\frac{0.123456}{2·10^{-6}}$
- $c_2=\frac{0.123454}{0.123454-0.123456}=-\frac{0.123454}{2·10^{-6}}$

$ϵ_{in}=c_1ϵ_1+c_2ϵ_2=2+2=4$