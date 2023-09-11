$\mathcal{L}(θ|x)=p_{θ}(x)=P(X=x|θ)$

Per variabili indipendenti e identicamente distribuite: $\mathcal{L}(θ|x)=∏\limits_{k=1}^{n}p_θ(x_i)$

Quale parametro ha la più alta probabilità di essere quello che era veramente? Ci sono diversi metodi
- Si prende il massimo della funzione di verosimiglianza
	- Questo probabilmente richiede di derivare la funzione e cercare di ottenere 0. A volte fa comodo aggiungere funzioni che non cambiano il massimo (come $\log$).
- La media campionaria $\frac{1}{n}∑\limits_{i=1}^{n}x_i^k$ è un ottimo stimatore del valore atteso (momento teorico, $E_θ[X^k]$). Quindi, il parametro $θ$ che soddisfa l'eguaglianza tra i momenti teorici ed empirici corrispondenti è probabilmente quello corretto.
	- Non sempre si può fare.

### Intervallo di fiducia

Un intervallo di fiducia per $θ$ è di livello $1-α$ se $P_θ(θ∈I)≥1-α$.

Per la media della distribuzione normale:
- $I=[\bar{X}_n±\frac{σ}{\sqrt{n}}q_{1-\frac{α}{2}}]$
	- Se non si conosce $σ$, allora $I=[\bar{X}_n±\frac{S_n}{\sqrt{n}}τ_{1-\frac{α}{2},n-1}]$
	- Se si vuole si può utilizzare intervalli con solo un estremo aleatorio, come $I=(-∞,\bar{X}_n+\frac{σ}{\sqrt{n}}q_{1-α}]$ (è sempre di livello $1-α$).
	- Grazie al teorema centrale del limite, per la media della distribuzione di Bernoulli (con $n$ grande): $I=[\bar{X}_n±\sqrt{\frac{\bar{X}_n(1-\bar{X}_n)}{n}}q_{1-\frac{α}{2}}]$

Per la varianza della distribuzione normale:
- $I=(0,\frac{(n-1)S_n^2}{χ^2_{α,n-1}})$ oppure $I=[\frac{(n-1)S_n^2}{χ^2_{1-α,n-1}},+∞)$
	- $χ_k^2$ ha la funzione di densità $f_ϰ(x)=\begin{cases}c_kx^{\frac{k}{2}-1}e^{-\frac{x}{2}} & x≥0 \\ 0 & x<0\end{cases}$