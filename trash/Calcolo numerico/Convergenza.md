Come trovare in quali punti una funzione è uguale a 0?

Metodi che richiedono due estremità $a$ e $b$, dove $f(a)$ è positiva e $f(b)$ è negativa (o viceversa):
- Bisezione
- Secanti

## Punto fisso

È un punto $α$ dove una funzione $g$ ha la proprietà $α=g(α)$.

È possibile che partendo da un punto $x_i$, si ottiene un $x_{i+1}=g(x_i)$ dove $|x_{i+1}-α|≤|x_i-α|$. In questo caso, si dice che la funzione *converge* verso $α$.

Questa è una proprietà desiderata se $f(α)=0$.

Affinché ci sia convergenza verso $α$ (e solo $α$), è necessario e sufficiente che $|g'(x)|<1$ in un intorno circolare chiuso di $α$. (Non è necessario al di fuori dell'intorno.)
- Se $0<g'(x)<1$, allora la successione è monotona crescente (se $x_0<a$) o monotona decrescente (se $x_0>a$).
- Se $-1<g'(x)<0$, allora la successione è alternata.
	- Assumendo che come $x_0$ venga scelta un'estremità del dominio, è possibile che $x_1$ si troverà fuori dal dominio. Si può risolvere il problema scegliendo come $x_0$ l'altra estremità.

>[!info]
L'**ordine di convergenza** verso $α$, è $p$ tale che:
>
>$\lim\limits_{i→∞}\frac{|x_{i+1}-α|}{|x_i-α|^p}=γ$
>
>Dove $γ>0$ (e se $p=1$, allora anche $γ<1$)

>[!note]
>Se intorno ad $α$, $g'(α)=g''(α)=…=g^{(p-1)}(α)=0$ e $g^{(p)}(α)≠0$, allora è garantito che l'ordine di convergenza di $g(x)$ sia almeno $p$.
>
>Questo perché, per via di Taylor, $x_{i+1}-α=g(x_i)-g(α)=\frac{(x_i-α)^p}{p!}g^{(p)}(ξ)\quad |x_i-ξ|<|x_i-α|$
>
>Quindi $\lim\limits_{i→∞}\frac{|x_{i+1}-α|}{|x_i-α|^p}=\frac{1}{p!}g^{(p)}(α)≠0$

#### Metodo delle tangenti

$x_{i+1}=x_i-\frac{f(x_i)}{f'(x_i)}$

In questo caso $g'(x)=1-\frac{f'(x)f'(x)-f(x)f''(x)}{f'(x)^2}=\frac{f(x)f''(x)}{f'(x)^2}$

Se $f'(α)≠0$, allora l'ordine di convergenza è almeno 2 (altrimenti è lineare).

>[!info]
>##### Convergenza in largo
>Intuitivamente, se $x_i$ è positivo in un punto della funzione convesso, oppure è negativo in un punto concavo, allora $x_{i+1}$ sarà più vicino ad $α$.
>Quindi, se:
>- $f(x_0)f''(x_0)>0$
>- $∀x∈[a,b]∖α\quad f'(x),f''(x)≠0$ (decrescenza/crescenza e convessità/concavità non cambiano nell'intervallo (meno $α$))

##### Metodo delle corde

Se elaborare $f'(x)$ è troppo costoso, si può "riciclare" il valore per $n$ passi:

$x_{i+1}=x_i-\frac{f(x_i)}{m}$

### Matrici

Data una matrice $A$ e un vettore $b$, si cerca il vettore $x$ tale che $Ax=b$.
Di solito si utilizzano metodo diretti, come quello di Gauss. Questo però ha una complessità $O(n^3)$, indipendentemente dal contenuto della matrice.
Questo è grave specialmente nelle matrici sparse, cioè quasi diagonali ma con pochi valori non nulli fuori dalle diagonali.

I metodi iterativi sono meno precisi ma possono essere più veloci, specialmente in questa situazione.

Presi $M$ e $N$ tali che $M$ non singolare, e $A=M-N$:
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
	- $J=D^{-1}(C+E)$.
	- $x^{(k+1)}=Jx^{(k)}+D^{-1}b$
	- $x_i^{(k+1)}=\frac{1}{a_{ii}}(b_i-∑\limits_{j=1,j≠i}^na_{ij}x_j^{(k)})$
- *Metodo di Gaudd-Seidel: $M=D-C$ e $N=E$
	- $G=(D-C)^{-1}E$
	- $x^{(k+1)}=Gx^{(k)}+(D-C)^{-1}b$
	- $x_i^{(k+1)}=\frac{1}{a_{ii}}(b_i-∑\limits_{j=1}^{i-1}a_{ij}x_j^{(k+1)}-∑\limits_{j=i+1}^na_{ij}x_j^{(k)})$
	- Il vettore $x$ può essere sostituito in-place, ma non si possono calcolare i suoi elementi in parallelo.
