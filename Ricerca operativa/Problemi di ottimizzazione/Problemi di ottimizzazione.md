# Problemi di ottimizzazione

$X \; \text{spazio delle soluzioni} \quad A \subseteq X \; \text{insieme delle soluzioni ammissibili (regione ammissibile)}$

$f:X \rightarrow R \quad \text{misura della "qualità" delle soluzioni (funzione obiettivo)}$

$(P) \quad min\{f(x):x \in A\}$

$\text{valore ottimo}=\text{estremo inferiore}\{f(x):x \in A\}$

$z^\star \in R \quad \text{valore ottimo di (P) se}$

- $z^\star \leq f(x) \; \forall x \in A$
- $z^\star \leq f(x) \; \forall x \in A \Rightarrow z \leq z^\star$

$x^\star \in X \text{soluzione ottima di (P) se}$

- $x^\star \in A$
- $f(x^\star) \leq f(x) \; \forall x \in A$

$x^\star \in A \; \text{è soluzione ottima} \iff f(x^\star) \; \text{valore ottimo}$

## Possibili situazioni

- $A= \emptyset \; \text{(valore ottimo} = +\infty)$
    - Esempio: $A=\{x \in \mathbb{R}: x \leq 0, x \geq 1\}$
- $\exists \; \text{valore ottimo} \; \exists \text{soluzione ottima}$
    - Esempio: $min\{x^2: x \in \mathbb{R}\}$
- $\exists \; \text{valore ottimo} \; \nexists \text{soluzione ottima}$
    - Esempio: $min\{e^{-x}: x \in \mathbb{R}\}$
- $\nexists \; \text{valore ottimo}$
    - Esempio: $min\{log(x): x > 0\}$
    - Problema inferiormente illimitato: $\text{(valore ottimo} = +\infty)$
    - $\forall k \in \mathbb{N} \; \exists x^k \in A : f(x^k) < -k$

## Classificazione problemi di ottimizzazione

- $X= \mathbb{R}^n$ *ottimizzazione continua*
- X finito/numerabile *ottimizzazione discreta* ($X \subseteq \mathbb{R}^n$)
    - $X=\{0,1\}^n$ *ottimizzazione combinatoria*
    - $X= \mathbb{Z}^n$ *ottimizzazione intera*
- $X= \mathbb{R}^{n_1} \times \mathbb{Z}^{n_2}$ *ottimizzazione mista*
- $f: X \rightarrow \mathbb{R}$
    - Lineare ($f(x)=cx=c_1x_1+c_2x_2+…+c_nx_n \; (c \in \mathbb{R}^n))$
    - Non lineare
- $A=\{x \in X : g_1(x) \leq 0,…,g_n(x) \leq 0\}$ (Minore/maggiore rimpiazzabili a piacimento)
    - $g_i:X \rightarrow \mathbb{R}$
        - Affine (= $f$ lineare + costante)
        - Non lineare

## Tipi di programmazione

- **Programmazione lineare**: $f$ lineare, $g_i$ affini
    - **Lineare intera**: $X= \mathbb{Z}^n, X=\{0,1\}^n$
    - Con le funzioni lineari, la soluzione ottima esiste sempre
- **Programmazione non lineare**: almeno una funzione è non lineare

## Esempi

- [[Esempio ottimizzazione pezzi ferrosi]]
- [[Esempio ottimizzazione wafer]]
- [[Problema dello zaino]]
- [[Bin packing]]