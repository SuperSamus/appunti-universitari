# Vincolo

# Vincolo di assegnamento/accoppiamento

$\{1,…,n\}$ oggetti

$\{1,…,m\}$ elementi

Oggetto → 1 solo elemento

Elemento → 1 solo oggetto

- $x_{ij} ∈ \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $∑\limits_{i=1}^n x_{ij}=1 \quad j=1…m$
- $∑\limits_{j=1}^n x_{ij}=1 \quad i=1…n$
- $n=m$

## Vincolo di semiassegnamento

- $x_{ij} ∈ \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $∑\limits_{j=1}^n x_{ij}=1 \quad i=1…n$

### Errore

$∑\limits_{j=1}^n ∑\limits_{i=1}^nx_{ij}=n$ non assicura che lo stesso oggetto non sia stato inserito più volte.

%%

## Vincolo di capacità

- $p_i>0$ "peso" dell'oggetto $i$
- $c_j>0$ capacità del contenitore $j$
- $x_{ij} ∈ \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $y_j ∈ \{0,1\} \quad y_j=\begin{cases} 1 &\text{se il contenitore } j \text{ viene usato} \\ 0 &\text{altrimenti} \end{cases}$
- $∑\limits_{i=1}^n p_ix_{ij} ≤ c_jy_j \quad j=1…n$

### Errore

$∑\limits_{i=1}^n p_i ≤ ∑\limits_{j=1}^n c_jy_j$ permette agli oggetti di essere smistati in modi impossibili.

### Funzione a carico fisso

$g(x)=\begin{cases} 0 &\text{se } x=0 \\ c+c_1x &\text{se } 0<x≤ L \end{cases}$

È brutta: non è lineare.

$f(x,y)=cy+c_1x \quad 0 ≤ x ≤ Ly \quad y ∈ \{0,1\}$

Piccola discrepanza: $y=1 \not ⇒ x=0$. Non ha molta importanza, dato che la funzione obiettivo si assicurerà che l'implicazione sia vera.
