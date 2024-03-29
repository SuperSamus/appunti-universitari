# Programmazione lineare

$f$ lineare, $g_i$ affini. Con le funzioni lineari, la soluzione ottima esiste sempre.

**Lineare intera**: $X= ℤ^n, X=\{0,1\}^n$

- Variabili: $x=(x_1,…,x_n)∈ℝ^n$
- Funzione obiettivo: $f(x)=c_1x_1+…+c_nx_n=c·x$
	- $c=(c_1,…,c_n)∈ℝ^n$
- Vincoli: $a_i·x=a_{i_1}x_1+…+a_{i_n}x_n \begin{matrix}≥ \\ ≤ \\ = \end{matrix}b_i$
	- $a_i=(a_{i_1},…,a_{i_n})∈ℝ^n$

## Formulazione canonica

^03350f

- Funzione obiettivo: $\max c·x$
- Vincolo: $Ax≤b$
	- $A_1·x≤b_1$
	- …
	- $A_m·x≤b_m$

$Ax=\begin{bmatrix} A_1·x \\ … \\ A_m·x \end{bmatrix}≤b$

Con:
- $A∈ℝ^{m×n}$ e $A_i∈ℝ^n$
- $x∈ℝ^n$
- $b∈ℝ^m$ e $b_i∈ℝ$
- $m≥n$ (numero di vincoli ≥ numero di variabili)

### Trasformazioni equivalenti

^4d0160

- $\min c·x≡-\max(-c)·x$
- $A_i·x=b_i≡A_i·x≤b_i∧A_ix≥b_i$
- $A_i·x≥b_i≡(-A_i)·x≤-b_i$
- $A_i·x≥b_i≡A_ix-s=b_i\quad s≥0$
- $A_i·x≤b_i≡A_ix+s=b_i\quad s≥0$

$s∈ℝ$ variabile di scarto

#### Esempio

$\max 2x_1+x_2$

Vincoli:
- $-x_1+x_2-x_3≤2$
- $x_1+x_2+x_4=5$
- $x_2+x_3=2$
- $x_1≥-4$
- $x_2,x_3,x_4≥0$

$x_4$ è usata solo per un vincolo (oltre a ≥0), quindi si può usare come variabile di scarto. $x_3$ si può usare come sostituzione ($x_3=2-x_2$).

1. $-x_1+2x_2≤4$
2. $x_1+x_2≤5$
3. $x_2≤2$
4. $-x_2≤0$
5. $-x_1≤4$

### Risolviamo

- $c=(2,1)$
- $b=\begin{bmatrix} 4 \\ 5 \\ 2 \\ 0 \\ 4 \end{bmatrix}$
- $A=\begin{bmatrix} -1 & 2 \\ 1 & 1 \\ 0 & 1 \\ 0 & -1 \\ -1 & 0 \end{bmatrix}$

Cercheremo la regione ammissibile: $P=\{x∈ℝ^n:Ax≤b\}$ poliedro (convesso).

![[Regione ammissibile 1.jpg]]

### Faccia

^14f224

Per alcuni $I⊆\{1,…,n\}$ si può associare una faccia del poliedro: $P_I=\{x∈P:A_ix=b_i \quad i∈I\}≠ ∅$ (se è $=∅$ non è una faccia).

Esempi (bisogna anche assicurarsi che i vincoli restino soddisfatti):
- $I=\{3\}→x_2=2$
- $I=\{2,4\}→x_1+x_2=5,x_2=0→P=\{(5,0)\}$ (vertice)
- $I=\{1,2\}→\begin{cases}-x_1+2x_2=4 \\ x_1+x_2=5 \end{cases}→P_{\{1,2\}}=∅$
	- L'intersezione $(2,3)$ non rientra nella regione ammissibile (non soddisfa il vincolo 3)
- $I=∅→P_∅=P$ (faccia "non propria")
- $I=\{1,4,5\}→P_{\{1,4,5\}}=\{(-4,0)\}$ (vertice)
	- $P_{\{1,4\}}=P_{\{1,5\}}=P_{\{4,5\}}=P_{\{1,4,5\}}$
	- Il vincolo 5 è completamente superfluo in questo caso, ma non è vero che, quando un punto è identificato da più di $n$ vincoli, uno di essi sia superfluo (anche se è vero con $n=2$)
		- Per esempio, in ℝ³, una piramide a base quadrata ha il vertice identificato da 4 vincoli

$\bar{x}∈P\quad I(\bar{x})=\{i:A_i\bar{x}=b_i\}$ (insieme degli indici dei *vincoli attivi* in $\bar{x}$)

Per esempio, $I((-4,0))=\{1,4,5\}$.

$A_I$ è la sottomatrice di $A$ ottenuta prendendo la righe $A_i$ per $i∈I$.

$A_{I(\bar{x})}$ è la sottomatrice di $A$ che contiene solo le righe i cui indici appartengono a $I(\bar{x})$.

$A_{I(\bar{x})}\bar{x}=b_{I(\bar{x})}$

Per esempio: $I=\{1,4\} \quad P_I=\{(-4,0)\} \quad A_I=\begin{bmatrix} A_1 \\ A_4 \end{bmatrix}=\begin{bmatrix} -1 & 2 \\ 0 & -1 \end{bmatrix}∈R^{2×2}$

Con $\bar{x}=(-4,0)$, abbiamo che $A_I\bar{x}=b_I$. Dato che la matrice è quadrata, $A_I$ può essere invertibile $→\bar{x}=A_I^{-1}b_I$.

### Vertice

^1cbebb

Faccia costituita da un solo punto.

Vertici ≡ Soluzioni di basi ammissibili

$B⊆\{1,…,m\}$ è una **base** se $\begin{cases} |B|=n \\ A_B∈R^{n×n}\text{ è invertibile}\end{cases}$

$A_Bx=b_B⤳x=A_B^{-1}b_B$ unica soluzione (**soluzione di base**) $→P_B=\begin{cases}\{A_B^{-1}b_B\} & \text{se }A_B^{-1}b_B\text{ è ammissibile} \\ ∅ & \text{se }A_B^{-1}b_B\text{ non è ammissibile}\end{cases}$

Esempio: $I=\{3,4\} \quad A_I=\begin{bmatrix} 0 & 1 \\ 0 & -1 \end{bmatrix}$ non è invertibile, quindi $\{3,4\}$ non è una base, e non crea quindi un vertice.

Attenzione, non tutti i poliedri hanno vertici, come $\{0≤x_2≤2\}$.

Se $rango(A)=n$, allora $P$ possiede almeno un vertice. Ricorda che alcune variabili sono eliminabili (abbiamo rimosso $x_3$ e $x_4$ per esempio), abbassando $n$.

### Involucro

#### Involucro convesso

Dati i punti $x^1,x^2,…,x^s∈ℝ^n$:

$conv(\{x^1,…,x^s\})=\{∑\limits^s_{i=1} λ_ix^i:λ_i≥0∧∑\limits^s_{i=1} λ_i=1\}$

Si può considerare un'interpolazione tra tutti i punti.

#### Involucro conico

^15fa21

Dati i vettori $v^1,v^2,…,v^t∈ℝ^n$:

$cono(\{v^1,…,v^t\})=\{∑\limits^t_{i=1} μ_iv^i:μ_i≥0\}$

Ogni vettore può essere allungato indipendentemente quanto si vuole (fino all'infinito).

### Decomposizione di poliedri (Motzkin 1936)

>[!important]
>$P$ è un poliedro
⇔
$∃x^1,…,x^s,v^1,…,v^t∈ℝ^n \text{ t.c. }P=conv(\{x^1,…,x^s\})+cono(\{v^1,…,v^t\})$

$X=\{x^1,…,x^s\},\quad V=\{v^1,…,v^t\}$

- $P=\{x∈ℝ^n:Ax≤b\}⇒cono(V)=\{v∈ℝ^n:Av≤\underline{0}\}$
- $v∈cono(V)⇔∀x∈P\quad ∀α≥0:x+αv∈P$
- $P$ limitato $⇔V=\{\underline{0}\}$
- Se $P$ possiede vertice, allora $X=\{\text{vertici}\}$

Con un problema simile a quello di prima, senza il vincolo 4, abbiamo:
![[Regione ammissibile 2.jpg]]

## Teorema fondamentale della programmazione lineare

Sia $P=conv(\{x^1,…,x^s\})+cono(\{v^1,…,v^t\})⊆ℝ^n$ un poliedro

>[!important]
$\max\{c·x:x∈P\}$ ha ottimo finito ⇔ $c·v^i≤0 \quad ∀i=1…t$.
In tal caso esiste $k∈\{1,…,s\}$ tale che $x^k$ è una soluzione ottima.

>[!info]
Prodotto scalare negativo vuol dire i vettori sono diversi di più di 90°

### Dimostrazione

Dato che $x=∑\limits^s_{i=1} λ_ix^i+∑\limits^t_{j=1}μ_jy^j$

$\max c·x≡\max ∑\limits^s_{i=1} λ_ic·x^i+∑\limits^t_{j=1}μ_jc·v^j$

Con $\begin{cases}x∈P \\ ∑\limits^s_{i=1} λ_i=1 \\ λ_i≥0 \\ μ_j≥0 \end{cases}$. Se accadesse che $c·v^i>0$, allora niente previene di mettere $μ_j→+∞$, rendendo il massimo infinito.
