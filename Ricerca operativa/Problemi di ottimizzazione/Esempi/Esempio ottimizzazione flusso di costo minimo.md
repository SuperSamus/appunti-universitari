# Esempio [[Problemi di ottimizzazione|ottimizzazione]] flusso di costo minimo

Gli archi hanno una capacità $u_{ij}$ e una costo di $c_{ij}$$.

```mermaid
flowchart LR
1 --> |2 2$| 2
1 --> |6 1$| 3
3 --> |5 4$| 2
3 --> |5 1$| 5
2 --> |6 1$| 4
5 --> |3 2$| 4
4 --> |2 2$| 6
5 --> |4 3$| 6
5 --> |4 -1$| 1
6 --> |2 -2$| 2
```

I $b_i$ sono:
- Sorgenti:
	- $-4$ per $i=1$
	- $-2$ per $i=5$
- Pozzi
	- $3$ per $i=4$
	- $3$ per $i=6$
- $0$ per tutto il resto

Abbiamo i soliti vincoli di [[ottimizzazione grafi]]. Se avere più di una sorgente o più di un pozzo può dare fastidio, basta immaginare una super sorgente $s$ con $b_s=-4-2=-6$ collegata a costo 0 alle vere sorgenti, e idem per i pozzi.

## Version più semplice

```mermaid
flowchart LR
1 --> |3 1$| 2
2 --> |2 1$| 3
1 --> |3 3$| 3
2 --> |3 5$| 4
3 --> |3 1$| 4
```

$x=(x_{ij})∈ℝ^n$ pseudoflusso se $0≤x_{ij}≤u_{ij}$