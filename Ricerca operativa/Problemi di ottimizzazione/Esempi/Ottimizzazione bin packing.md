# [[Problemi di ottimizzazione|Ottimizzazione]] bin packing/impacchettamento

Abbiamo n oggetti da infilare in m contenitori.

- $p_i>0$ "peso" dell'oggetto $i$
- $c_j$ capacità del contenitore $j$

Dobbiamo infilare tutti gli oggetti usando meno contenitori possibili.

Per ogni oggetto, dobbiamo scegliere in quale contenitore inserirlo. Oppure, preso un oggetto e un contenitore, decidiamo se inserirlo o meno.

- $x_{ij} ∈ \{0,1\}$, $x_{ij}=\begin{cases} 1 &\text{se } i → j \\ 0 &\text{altrimenti} \end{cases}$
- $y_j ∈ \{0,1\}$, $y_j=\begin{cases} 1 &\text{se usiamo il contenitore } j \\ 0 &\text{altrimenti} \end{cases}$

$y_j$ non è "necessario", ma lo sfruttiamo per la funzione obiettivo. Di conseguenza, bisogna ricordarsi di usarlo anche nei vincoli.

Vincoli[^1]:
- Vincolo di semiassegnamento: $∑\limits_{j=1}^n x_{ij}=1 \quad i=1…n$
- Vincolo di capacità: $∑\limits_{i=1}^n p_ix_{ij} ≤ c_jy_j \quad j=1…n$

Funzione obiettivo min: $∑\limits_{i=1}^n y_i$

### Esempio

| i   | $p_i$ |
| --- | ----- |
| 1   | 5     |
| 2   | 2     |
| 3   | 5     |
| 4   | 6     |

| j   | $c_j$ |
| --- | ---- |
| 1   | 9    |
| 2   | 6    |
| 3   | 9    |

Se non ci fosse stato il vincolo di interezza ($x_{ij} ∈ \{0,1\}$), potevamo fare con solo 2 contenitori:

- $c_1=5\frac{1}{2}+2\frac{1}{2}+5\frac{1}{2}+6\frac{1}{2}$
- $c_3=5\frac{1}{2}+2\frac{1}{2}+5\frac{1}{2}+6\frac{1}{2}$


[^1]: Errori possibili:
	- Vincolo di semiassegnamento sbagliato: $∑\limits_{j=1}^n ∑\limits_{i=1}^nx_{ij}$ non assicura che lo stesso oggetto sia stato inserito più volte.
	- Vincolo di capacità sbagliato: $∑\limits_{i=1}^n x_i ≤ ∑\limits_{j=1}^n c_jy_j$ permette agli oggetti di essere smistati in modi impossibili.
