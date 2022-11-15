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

- $A= ∅ \; \text{(valore ottimo} = +∈fty)$
    - Esempio: $A=\{x ∈ ℝ: x ≤ 0, x ≥ 1\}$
- $∃ \text{valore ottimo} \; ∃ \text{soluzione ottima}$
    - Esempio: $min\{x^2: x ∈ ℝ\}$
- $∃ \text{valore ottimo} \; ∄\text{soluzione ottima}$
    - Esempio: $min\{e^{-x}: x ∈ ℝ\}$
- $\nexists \text{valore ottimo}$
    - Esempio: $min\{log(x): x > 0\}$
    - Problema inferiormente illimitato: $\text{(valore ottimo} = +∈fty)$
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

$Ax=\begin{bmatrix} A_1·x \\ ... \\ A_m·x \end{bmatrix}≤b$

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

### Programmazione non lineare

Almeno una funzione è non lineare.
