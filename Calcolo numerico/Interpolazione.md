Viene utilizzata per semplificare una funzione $f(x)$ complessa e renderla più "trattabile", o per ottenere una funzione quando non ce n'è una.

Chiamando $p(x)$ l'approssimazione di $f(x)$, l'interpolazione viene fatta in $n$ specifici punti della funzione. Per avere l'approssimazione "migliore possibile", si cerca di minimizzare il *resto* negli $n$ punti $x_i$:
$r_i=f(x_i)-p(x_i)$
Minimi quadrati: $\min ||r||_2$

### Polinomio di interpolazione

Un tipo di interpolazione dove $||r||_2=0$.
Dati $n$ punti $x_i$ diversi, esiste ed è unico il polinomio:
$p(x)=a_1+a_2x+…+a_{n-1}x^{n-2}+a_nx^{n-1}$
Che soddisfa $∀i\;p(x_i)=f(x_i)$.

I coefficienti possono essere trovati risolvendo:
$Va=f$

Dove:
- $f$ è il vettore dei $f(x_i)$
- $V=x_{i}^{j}$ è la *matrice di Vandermonde*

$det(V)=∏\limits_{i>j}(x_i-x_j)$
Essendo diverso da 0, questo dimostra esistenza e unicità.

$V$ è però una matrice malcondizionata. Per questo è spesso meglio usare:

#### Interpolazione di Lagrange

$p(x)=∑\limits_jf(x_j)L_j(x)$

Dove $L_j(x)=∏\limits_{k≠j}\frac{x-x_k}{x_j-x_k}$

Dimostrazione che $∀i\;p(x_i)=f(x_i)$:
$L_j(x_i)=\begin{cases}1 & i=j \\ 0 & i≠j\end{cases}$

Caso $n=2$, interpolazione lineare:
$$p(x)=f(x_1)\frac{x-x_2}{x_1-x_2}+f(x_2)\frac{x-x_1}{x_2-x_1}=\frac{f(x_2)(x-x_1)+f(x_1)(x_2-x)}{x_2-x_1}$$

### Resto

Dati $n$ unti $x_i$ presi da una $f$ derivabile $n$ volte, $a=\min x_i$ e $b=\max x_i$, esiste un $ξ∈(a,b)$ tale che:
$r(x)=\frac{f^{(n)}(ξ)}{n!}∏(x-x_i)$

>[!warning]
>Più punti *non* implicano una migliore interpolazione.
>
>Esempio tipico, *funzione di Runge*:
>$f(x)=\frac{1}{1-x^2}\quad x∈[-1,1]$
>
>La situazione peggiora nel caso non si conosca $f$, e i punti conosciuti sono affetti da rumore. In questo caso, è meglio minimizzare l'errore di un polinomio di grado più basso (e.g. regressione lineare).
