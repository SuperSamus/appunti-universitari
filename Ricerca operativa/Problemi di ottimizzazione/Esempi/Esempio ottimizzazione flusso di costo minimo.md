# Esempio [[Problemi di ottimizzazione|ottimizzazione]] flusso di costo minimo

Gli archi hanno una capacità $u_{ij}$ e una costo di $c_{ij}$$ per ogni unità trasportata.

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
	- $b_1=-4$
	- $b_5=-2$
- Pozzi
	- $b_4=b_6=3$
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

- $b_1=-5$
- $b_4=5$

Proviamo a vedere questo flusso (invalido), di costo 6$:

```mermaid
flowchart LR
1 ==> |2/3 1$| 2
2 ==> |2/2 1$| 3
1 --> |0/3 3$| 3
2 --> |0/3 5$| 4
3 ==> |2/3 1$| 4
```

Ciò creerà questo [[Ottimizzazione trasporto massimo#^8639e2|grafo residuo]]:

```mermaid
flowchart LR
1 --> |1 1$| 2
1 <-- |2 -1$| 2
2 <-- |2 -1$| 3
1 --> |3 3$| 3
2 --> |3 5$| 4
3 --> |1 1$| 4
3 <-- |2 -1$| 4
```

Proviamo ad aggiungere un'unità di flusso per $1→3→4$:

```mermaid
flowchart LR
1 --> |2/3 1$| 2
2 --> |2/2 1$| 3
1 ==> |1/3 3$| 3
2 --> |0/3 5$| 4
3 ==> |3/3 1$| 4
```

Costo $=6+1+3=10$, ma mancano ancora 2 unità.

Grafo residuo:

```mermaid
flowchart LR
1 --> |1 1$| 2
1 <-- |2 -1$| 2
2 <-- |2 -1$| 3
1 --> |2 3$| 3
1 <-- |1 -3$| 3
2 --> |3 5$| 4
3 <-- |3 -1$| 4
```


Spingiamo un'altra unità per $1→2→4$:


```mermaid
flowchart LR
1 ==> |3/3 1$| 2
2 --> |2/2 1$| 3
1 --> |1/3 3$| 3
2 ==> |1/3 5$| 4
3 --> |3/3 1$| 4
```

Costo $=10+3+5=18$, manca un'ultima unità.

Grafo residuo:

```mermaid
flowchart LR
1 <-- |3 -1$| 2
2 <-- |2 -1$| 3
1 --> |2 3$| 3
1 <-- |1 -3$| 3
2 --> |2 5$| 4
2 --> |1 -5$| 4
3 <-- |3 -1$| 4
```

Il grafo mostra chiaramente un unico cammino rimasto per l'ultima unità: $1→3→2→4$.

```mermaid
flowchart LR
1 --> |3/3 1$| 2
2 ==> |1/2 1$| 3
1 ==> |2/3 3$| 3
2 ==> |2/3 5$| 4
3 --> |3/3 1$| 4
```

Costo: $18+3-1+5=25$.

$x=(x_{ij})∈ℝ^n$ pseudoflusso se $0≤x_{ij}≤u_{ij}$