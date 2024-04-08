Come trovare in quali punti una funzione è uguale a 0?

Metodi che richiedono due estremità $a$ e $b$, dove $f(a)$ è positiva e $f(b) è negativa (o viceversa):
- Bisezione
- Secanti

## Punto fisso

Dato $x^*$ il punto ricercato, $x=g(x)$.
Itera con $x_{i+1}=g(x_i)$, se la funzione converge verso $x^*$.

Per assicurare la convergenza, serve che $|g'(x)|<1$ nel raggio dove si itera.

>[!info]
L'ordine di convergenza verso $α$, è $p$ tale che:
>
>$\lim\limits_{i→∞}\frac{|x_{i+1}-α|}{|x_i-α|^p}=γ$
>
>Dove $γ>0$ (e se $p=1$, allora anche $γ<1$)

>[!note]
>Se intorno ad $α$, $g'(α)=g''(α)=…=g^{(p-1)}(α)=0$ e $g^{(p)}(α)≠0$, allora è garantito che l'ordine di convergenza di $g(x)$ sia almeno $p$.
>
>Questo perché, per via di Taylor, $x_{i+1}-α=g(x_i)-g(α)=\frac{(x_i-α)^p}{p!}g^{(p)}(ξ)$
>
>Quindi $\lim\limits_{i→∞}\frac{|x_{i+1}-α|}{|x_i-α|^p}=\frac{1}{p!}g^{(p)}(α)≠0$

#### Metodo delle tangenti

$x_{i+1}=x_i-\frac{f(x_i)}{f'(x_i)}$

In questo caso $g'(x)=\frac{f(x)f''(x)}{f'(x)^2}$

### Matrici

I metodi iterativi sono utili in matrici sparse (cioè quasi diagonali, ma con pochi valori non nulli sparsi in giro).
Presi $M$ e $N$ tali che $A=M-N$:
$b=Mx-Nx$
$x=