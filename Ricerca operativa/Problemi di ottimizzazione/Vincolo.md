# Vincolo

# Vincolo di assegnamento/accoppiamento

$\{1,…,n\}$ oggetti

$\{1,…,m\}$ elementi

Oggetto → 1 solo elemento

Elemento → 1 solo oggetto

- $x_{ij} \in \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $\displaystyle\sum_{i=1}^n x_{ij}=1 \quad j=1…m$
- $\displaystyle\sum_{j=1}^n x_{ij}=1 \quad i=1…n$
- $n=m$

## Vincolo di semiassegnamento

- $x_{ij} \in \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $\displaystyle\sum_{j=1}^n x_{ij}=1 \quad i=1…n$

### Errore

$\displaystyle\sum_{j=1}^n \displaystyle\sum_{i=1}^nx_{ij}=n$ non assicura che lo stesso oggetto non sia stato inserito più volte.

## Vincolo di capacità

- $p_i>0$ "peso" dell'oggetto $i$
- $c_j$ capacità del contenitore $j$
- $\displaystyle\sum_{i=1}^n p_ix_{ij} \leq c_jy_j \quad j=1…n$

### Errore

$\displaystyle\sum_{i=1}^n x_i \leq \displaystyle\sum_{j=1}^n c_jy_j$ permette agli oggetti di essere smistati in modi impossibili.

### Funzione a carico fisso

$g(x)=\begin{cases} 0 &\text{se } x=0 \\ c+c_1x &\text{se } 0<x\leq L \end{cases}$

È brutta: non è lineare.

$f(x,y)=cy+c_1x \quad 0 \leq x \leq Ly \quad y \in \{0,1\}$

Piccola discrepanza: $y=1 \not \Rightarrow x=0$. Non ha molta importanza, dato che la funzione obiettivo si assicurerà che l'implicazione sia vera.
