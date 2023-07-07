# Probabilità sulla retta reale

Vediamo due classi principali di esempi di probabilità su Ω=ℝ.

Questi due classi non esauriscono i possibili esempi di probabilità su ℝ, ma nelle applicazioni vedremo sempre queste due classi.

## 1° classe di esempi: probabilità discrete

Una probabilità discreta su Ω=ℝ è una probabilità su Ω=ℝ, $𝔉=\mathcal{P}(ℝ)$, che sia concentrata su una successione finita o numerabile di punti $x_0,x_1,x_2,…$

Ad esempio, la probabilità associata al n° di "testa" in due lanci di moneta è una probabilità discreta, concentrata su $\{0,1,2\}=\{x_1,x_2,x_3\}$

Chiamami $p_i:=p(x_i):=P(\{x_i\})$, allora:

$P(A)=∑\limits_{x_i∈A}p(x_i)$
(serie se ∃ infiniti $x_i∈A$)

Definizione: la funzione $p:\{x_1,x_2,…\}→ℝ,p(x_i)=P(\{x_i\})$ si dice funzione di massa, o densità discreta, di P.

Osservazione:
- $p$ soddisfa:
	- $p(x_i)≥0$
	- $∑\limits_{i}p(x_i)=P(ℝ)=1$
- Viceversa, dati una successione $x_1,x_2,…$ finita o numerabile e una funzione $p$ con le proprietà sopra, allora esiste un'unica probabilità $P$ su ℝ avente $p$ come funzione di massa.
- In particolare, dalla formula (Δ), è possible calcolare P(A) a partire solo dalla successione e dalla funzione di massa.
- Si definisce $p$ su tutto ℝ, ponendo $p(x)=0$ per $x≠x_i$

TODO
