# Problemi di ottimizzazione

- $X$ spazio delle soluzioni
	- $A ⊆ X$ insieme delle soluzioni ammissibili (regione ammissibile)
- $f:X → R$ misura della "qualità" delle soluzioni (funzione obiettivo)
- $(P) \quad \min\{f(x):x ∈ A\}$
- **Valore ottimo**: estremo inferiore di $\{f(x):x ∈ A\}$
	* *$z^* ∈ R$ valore ottimo di $(P)$ se
		- $z^* ≤ f(x) \; ∀x ∈ A$
		- $z ≤ f(x) \; ∀x ∈ A ⇒ z ≤ z^*$
	* *$x^* ∈ X$ soluzione ottima di $(P)$ se
		- $x^* ∈ A$
		- $f(x^*) ≤ f(x) \; ∀x ∈ A$

$x^* ∈ A \text{ è soluzione ottima} ⟺ f(x^*) \; \text{valore ottimo}$

## Possibili situazioni

- $A = ∅$ (valore ottimo = +∞)
	- Esempio: $A=\{x ∈ ℝ: x ≤ 0, x ≥ 1\}$
- ∃ valore ottimo e ∃soluzione ottima
	- Esempio: $\min\{x^2: x ∈ ℝ\}$
- ∃ valore ottimo e ∄ soluzione ottima
	- Esempio: $\min\{e^{-x}: x ∈ ℝ\}$
- ∄ valore ottimo
	- Esempio: $\min\{log(x): x > 0\}$
	- Problema inferiormente illimitato: (valore ottimo = −∞)
	- $∀k ∈ ℕ \; ∃ x^k ∈ A : f(x^k) < -k$

## Classificazione problemi di ottimizzazione

- $X= ℝ^n$ *ottimizzazione continua*
- X finito/numerabile *ottimizzazione discreta* ($X ⊆ ℝ^n$)
	- $X=\{0,1\}^n$ *ottimizzazione combinatoria*
	- $X= ℤ^n$ *ottimizzazione intera*
- $X= ℝ^{n_1} ⨉ ℤ^{n_2}$ *ottimizzazione mista*

$f: X → ℝ$
- Lineare ($f(x)=cx=c_1x_1+c_2x_2+…+c_nx_n \; (c ∈ ℝ^n))$
- Non lineare
	- Esempio: $f(t)=max\{t,2t\}=\begin{cases} 2t &\text{se } t ≥ 0 \\ t &\text{se } t < 0 \end{cases}$

$A=\{x ∈ X : g_1(x) ≤ 0,…,g_n(x) ≤ 0\}$ (Minore/maggiore rimpiazzabili a piacimento)
- $g_i:X → ℝ$
	- Affine (= $f$ lineare + costante)
	- Non lineare

## Tipi di programmazione

- **[[Programmazione lineare]]**: $f$ lineare, $g_i$ affini
    - **Lineare intera**: $X=ℤ^n, X=\{0,1\}^n$
    - Con le funzioni lineari, la soluzione ottima esiste sempre
- **Programmazione non lineare**: almeno una funzione è non lineare
