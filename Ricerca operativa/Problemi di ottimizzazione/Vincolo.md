# Vincolo

# Vincolo di assegnamento/accoppiamento

$\{1,…,n\}$ oggetti

$\{1,…,m\}$ elementi

Oggetto → 1 solo elemento

Elemento → 1 solo oggetto

- $x_{ij} \in \{0,1\}$, $x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $\displaystyle\sum_{i=1}^n x_{ij}=1 \quad j=1…m$
- $\displaystyle\sum_{j=1}^n x_{ij}=1 \quad i=1…n$
- $n=m$

## Vincolo di semiassegnamento

- $x_{ij} \in \{0,1\}$, $x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $\displaystyle\sum_{j=1}^n x_{ij}=1 \quad i=1…n$

### Errore

$\displaystyle\sum_{j=1}^n \displaystyle\sum_{i=1}^nx_{ij}=n$ non assicura che lo stesso oggetto non sia stato inserito più volte.

%%

## Vincolo di capacità

- $\displaystyle\sum_{i=1}^n p_ix_{ij} \leq c_jy_j \quad j=1…n$

### Errore

$\displaystyle\sum_{i=1}^n x_i \leq \displaystyle\sum_{j=1}^n c_jy_j$ permette agli oggetti di essere smistati in modi impossibili.
%%
