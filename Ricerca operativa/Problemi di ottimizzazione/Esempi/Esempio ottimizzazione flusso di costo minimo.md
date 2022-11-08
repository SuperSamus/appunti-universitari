# Esempio [[Problemi di ottimizzazione|ottimizzazione]] flusso di costo minimo

[[Ottimizzazione grafi]] su questo grafo, ma gli archi costano:

```mermaid
flowchart LR
1 --> |2 2$| 2
1 --> |1 6$| 3
3 --> |4 5$| 2
3 --> |1 5$| 5
2 --> |1 6$| 4
5 --> |2 3$| 4
4 --> |2 2$| 6
5 --> |3 4$| 6
5 --> |-1 3$| 1
6 --> |-2 2$| 2
```

I $b_i$ sono:
- $-4$ per $i=1$
- $-2$ per $i=5$
- $3$ per $i=4$
- $3$ per $i=6$
- $0$ per tutto il resto

$x=(x_{ij})∈ℝ^n$ pseudoflusso se $0≤x_{ij}≤u_{ij}$