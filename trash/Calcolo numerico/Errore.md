Errore totale:
- $ϵ_{tot}≐ϵ_{alg}+ϵ_{in}$
- $ϵ_{tot}=\frac{ψ(\tilde{x})-f(x)}{f(x)}$

### Errore inerente

$ϵ_{in}=\frac{f(\tilde{x})-f(x)}{f(x)}$

- Errore relativo: $ϵ_x=\frac{\tilde{x}-x}{x}$
- Coefficiente di amplificazione: $c_x=\frac{xf'(x)}{f(x)}$
- $ϵ_{in}≐c_xϵ_x$

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

### Errore algoritmico

$ϵ_{alg}=\frac{ψ(\tilde{x})-f(\tilde{x})}{f(\tilde{x})}$

Dipende dalla serie di operazioni eseguite nell'aritmetica finita.

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

$ϵ_{in}≐c_1ϵ_1+c_2ϵ_2=2+2=4$

La sottrazione è estremamente dannosa. Se è parte dell'errore algoritmico, si cerca di evitarla il più possibile.
Per esempio, nelle equazioni di secondo grado $ax^2+bx+c=0$, dove $x_1=\frac{-b+\sqrt{b^2-4ac}}{2a}$ (assumendo $b$ positivo), si approfitta invece della proprietà $x_1x_2=\frac{c}{a}$.

### Errore analitico

Data una funzione non razionale $f(x)$, si deve utilizzare un'approssimazione razionale $g(x)$ per eseguire i calcoli, che si aggiunge all'errore totale:
$ϵ_{an}=\frac{g(x)-f(x)}{f(x)}$

Un'approssimazione più precisa (per esempio, $n$ più alto nell'approssimazione di Taylor) riduce l'errore analitico, ma aumenterà l'errore algebrico.
È importante trovare il giusto equilibrio per minimizzare $ϵ_{alg}+ϵ_{an}$.
