Viene utilizzata per semplificare una funzione $f(x)$ complessa e renderla più "trattabile", o per ottenere una funzione quando non ce n'è una.

Chiamando $p(x)$ l'approssimazione di $f(x)$, l'interpolazione viene fatta in $n$ specifici punti della funzione. Per avere l'approssimazione "migliore possibile", si cerca di minimizzare il *resto* negli $n$ punti $x_i$:
$r_i=f(x_i)-p(x_i)$
Minimi quadrati: $\min ||r||_2$

### Polinomio di interpolazione

Un tipo di interpolazione dove $||r||_2=0$.
Dati $n$ punti $x_i$ diversi, esiste ed è unico il polinomio:
$p(x)=a_1x^{n-1}+a_2x^{n-2}+…+a_{n-1}x+a_n$
Che soddisfa $∀i\;p(x_i)=f(x_i)$.

I coefficienti possono essere trovati risolvendo:
$Va=f$

Dove $V=x_{i-1}^{n-j}$ è la *matrice di Vandermonde*: