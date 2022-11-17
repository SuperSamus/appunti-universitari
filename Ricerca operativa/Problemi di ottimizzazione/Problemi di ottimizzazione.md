# Problemi di ottimizzazione

- $X$ spazio delle soluzioni
	- $A ⊆ X$ insieme delle soluzioni ammissibili (regione ammissibile)
- $f:X → R$ misura della "qualità" delle soluzioni (funzione obiettivo)
- $(P) \quad min\{f(x):x ∈ A\}$
- **Valore ottimo**: $∈f\{f(x):x ∈ A\}$
	* *$z^* ∈ R$ valore ottimo di $(P)$ se
		- $z^* ≤ f(x) \; ∀x ∈ A$
		- $z^* ≤ f(x) \; ∀x ∈ A ⇒ z ≤ z^*$
	* *$x^* ∈ X$ soluzione ottima di $(P)$ se
		- $x^* ∈ A$
		- $f(x^*) ≤ f(x) \; ∀x ∈ A$

$x^* ∈ A \text{ è soluzione ottima} ⟺ f(x^*) \; \text{valore ottimo}$

## Possibili situazioni

- $A = ∅$ (valore ottimo = +∞)
	- Esempio: $A=\{x ∈ ℝ: x ≤ 0, x ≥ 1\}$
- ∃ valore ottimo e ∃soluzione ottima
	- Esempio: $min\{x^2: x ∈ ℝ\}$
- ∃ valore ottimo e ∄ soluzione ottima
	- Esempio: $min\{e^{-x}: x ∈ ℝ\}$
- ∄ valore ottimo
	- Esempio: $min\{log(x): x > 0\}$
	- Problema inferiormente illimitato: (valore ottimo = −∞)
	- $∀k ∈ ℕ \; ∃ x^k ∈ A : f(x^k) < -k$

## Classificazione problemi di ottimizzazione

- $X= ℝ^n$ *ottimizzazione continua*
- X finito/numerabile *ottimizzazione discreta* ($X ⊆ ℝ^n$)
	- $X=\{0,1\}^n$ *ottimizzazione combinatoria*
	- $X= ℤ^n$ *ottimizzazione intera*
- $X= ℝ^{n_1} ⨉ ℤ^{n_2}$ *ottimizzazione mista*
- $f: X → ℝ$
	- Lineare ($f(x)=cx=c_1x_1+c_2x_2+…+c_nx_n \; (c ∈ ℝ^n))$
	- Non lineare
		- Esempio: $f(t)=max\{t,2t\}=\begin{cases} 2t &\text{se } t ≥ 0 \\ t &\text{se } t < 0 \end{cases}$
- $A=\{x ∈ X : g_1(x) ≤ 0,…,g_n(x) ≤ 0\}$ (Minore/maggiore rimpiazzabili a piacimento)
	- $g_i:X → ℝ$
		- Affine (= $f$ lineare + costante)
		- Non lineare

## Tipi di programmazione

### Programmazione lineare

$f$ lineare, $g_i$ affini. Con le funzioni lineari, la soluzione ottima esiste sempre.

**Lineare intera**: $X= ℤ^n, X=\{0,1\}^n$

- Variabili: $x=(x_1,…,x_n)∈ℝ^n$
- Funzione obiettivo: $f(x)=c_1x_1+…+c_nx_n=c·x$
	- ($c=(c_1,…,c_n)∈ℝ^n$)
- Vincoli: $a_i·x=a_{i_1}x_1+…+a_{i_n}x_n \begin{matrix}≥ \\ = \\ ≤ \end{matrix}$
	- $a_i=(a_{i_1},…,a_{i_n})∈ℝ^n$

#### Formulazione canonica

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
- $m≥n$ (il numero di vincoli è ≥ il numero di variabili)

##### Trasformazioni equivalenti

- $\min c·x≡-\max(-c)·x$
- $A_i·x=b_i≡A_i·x≤b_i∧A_ix≥b_i$
- $A_i·x≥b_i≡(-A_i)·x≤-b_i$
- $A_i·x≥b_i≡A_ix-s=b_i\quad s≥0$
- $A_i·x≤b_i≡A_ix+s=b_i\quad s≥0$

$s∈ℝ$ variabile di scarto

###### Esempio

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

##### Risolviamo

- $c=(2,1)$
- $b=\begin{bmatrix} 4 \\ 5 \\ 2 \\ 0 \\ 4 \end{bmatrix}$
- $A=\begin{bmatrix} -1 & 2 \\ 1 & 1 \\ 0 & 1 \\ 0 & -1 \\ -1 & 0 \end{bmatrix}$

Cercheremo la regione ammissibile: $P=\{x∈ℝ^n:Ax≤b\}$ poliedro.

![[Regione ammissibile.jpg]]

##### Faccia

Per alcuni $I⊆\{1,…,n\}$ si può associare una faccia del poliedro: $P_I=\{x∈P:A_ix=b_i \quad i∈I\}≠ ∅$ (se è $=∅$ non è una faccia).

Esempi (bisogna anche assicurarsi che i vincoli restino soddisfatti):
- $I=\{3\}→x_2=2$
- $I=\{2,4\}→x_1+x_2=5,x_2=0→P=\{(5,0)\}$
	-  È un **vertice**: faccia costituita da un solo punto
- $I=\{1,2\}→\begin{cases}-x_1+x_2=4 \\ x_1+x_2=5 \end{cases}→P_{\{1,2\}}=∅$
- $I=∅→P_∅=P$ (faccia "non propria")
- $I=\{1,4,5\}→P_{\{1,4,5\}}=\{(-4,0)\}$ (vertice)
	- $P_{\{1,4\}}=P_{\{1,5\}}=P_{\{4,5\}}=P_{\{1,4,5\}}$
	- Il vincolo 5 è superfluo in questo caso, ma quando un punto è identificato da più di $n$ vincoli, non è vero che è un vincolo sia necessariamente superfluo (anche se è vero con $n=2$)
		- Per esempio, in ℝ³, una piramide a base quadrata ha il vertice identificato 4 volte.

$\bar{x}∈P\quad I(\bar{x})=\{i:A_i\bar{x}=b_i\}$ (insieme degli indici dei *vincoli attivi* in $\bar{x}$)

Per esempio, $I((-4,0))=\{1,4,5\}$.

$A_I$ è la sottomatrice di $A$ ottenuta prendendo la righe $A_i$ per $i∈I$.

$A_{I(\bar{x})}$ è la sottomatrice di $A$ che contiene solo le righe i cui indici appartengono a $I(\bar{x})$.

$A_{I(\bar{x})}\bar{x}=b_{I(\bar{x})}$

Per esempio: $I=\{1,4\} \quad P_I=\{(-4,0)\} \quad A_I=\begin{bmatrix} A_1 \\ A_4 \end{bmatrix}=\begin{bmatrix} -1 & 2 \\ 0 & -1 \end{bmatrix}∈R^{2×2}$

Con $\bar{x}=(-4,0)$, abbiamo che $A_I\bar{x}=b_I$. Dato che la matrice è quadrata, $A_I$ può essere invertibile $→\bar{x}=A_I^{-1}b_I$

$B⊆\{1,...,m\}$ è una **base** se $\begin{cases} |B|=n \\ A_B∈R^{n×n}\text{ è invertibile}\end{cases}$

$A_Bx=b_B⤳x=A_B^{-1}b_B$ unica soluzione (**soluzione di base**) $→P_B=\begin{cases}\{A_B^{-1}b_B\} & \text{se }A_B^{-1}b_B\text{ è ammissibile} \\ ∅ & \text{se }A_B^{-1}b_B\text{ non è ammissibile}\end{cases}$

Vertici ≡ Soluzioni di basi ammissibili

Esempio: $I=\{3,4\} \quad A_I=\begin{bmatrix} 0 & 1 \\ 0 & -1 \end{bmatrix}$ non è invertibile, quindi $\{3,4\}$ non è una base, e non crea quindi un vertice.

Attenzione, non tutti i poliedri hanno vertici, come $\{0≤x_2≤2\}$.

Se $rango(A)=n$, allora $P$ possiede almeno un vertice. Ricorda che alcune variabili sono eliminabili (abbiamo rimosso $x_3$ e $x_4$ per esempio), abbassando $n$.

### Programmazione non lineare

Almeno una funzione è non lineare.
