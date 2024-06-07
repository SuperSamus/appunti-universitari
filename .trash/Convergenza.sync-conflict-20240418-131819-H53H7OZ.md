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
$Ax=b$
$b=Mx-Nx$
$x=M^{-1}Nx+M^{-1}b$
$x=Px+q$

Dove $P=M^{-1}N$ e $q=M^{-1}b$

Alcuni condizioni sufficienti per la convergenza:
- $ρ(P)<1$
- Esiste una [[norma]] matriciale dove $∥P∥<1$

Si può dimostrare applicando queste funzioni all'errore $e^{(i)}=|x^*-x^{(i)}|$, dato che: $e^{(i+1)}=Pe^{(i)}$, e vogliamo che $\lim\limits_{i→∞}e_i=0$.


#### Composizioni da particolari

Dato $D$ la parte diagonale di $A$, $-C$ la parte diagonale inferiore (esclusiva) di $A$, e $-E$ la parte diagonale superiore (esclusiva) di A.

$A=D-C-E$

- *Metodo di Jacobi*: $M=D$ e $N=C+E$
L'iterazione si può quindi calcolare (per riga $i$):
$x_i^{(k+1)}=\frac{1}{a_{ii}}(b_i-∑\limits_{j=1,j≠i}^na_{ij}x_j^{(k)})$

- *Metodo di Gaudd-Seidel: $M=D-C$ e $N=E$
L'iterazione si può quindi calcolare (per riga $i$):
$x_i^{(k+1)}=\frac{1}{a_{ii}}(b_i-∑\limits_{j=1}^{i-1}a_{ij}x_j^{(k+1)}-∑\limits_{j=i+1}^na_{ij}x_j^{(k)})$

Il vettore $x$ può essere sostituito in-place, ma non si possono calcolare i suoi valori in parallelo.