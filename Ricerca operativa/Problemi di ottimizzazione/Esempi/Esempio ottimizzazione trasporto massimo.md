# Esempio ottimizzazione trasporto massimo

```mermaid
flowchart LR
1 -- 6 --> 2 -- 5 --> 4 -- 6 --> 7
1 -- 1 --> 6 -- 4 --> 4 -- 1 --> 5
1 -- 4 --> 3 -- 4 --> 5 -- 5 --> 7
3 -- 2 --> 6
```

L'obiettivo è di trasportare la maggior quantità di flusso possibile da $1$ e $7$. Tuttavia, i tubi hanno una capacità massima nel trasporto di acqua, e tutti gli altri nodi non ammettono di ricevere più acqua di quella mandano (e ovviamente anche il contrario). Come si distribuisce il flusso?

Dati:
- $s=1$ origine
- $t=7$ destinazione
- $b_i = \begin{cases} -V &\text{se } i=s \\ V &\text{se } i=t \\ 0 &\text{altrimenti} \end{cases}$

Funzione obiettivo max: $V$

Proviamo una soluzione ammissibile:

```mermaid
flowchart LR
1 -- 3/6 --> 2 -- 3/5 --> 4 -- 6/6 --> 7
1 -- 1/1 --> 6 -- 3/4 --> 4 -- 0/1 --> 5
1 -- 4/4 --> 3 -- 2/4 --> 5 -- 2/5 --> 7
3 -- 2/2 --> 6
```

In questo caso la soluzione ammissibile è $V=8$. Si può fare di meglio?

Si potrebbe aumentare la quantità di flusso lungo questo cammino orientato: $P=\{1,2,4,5,7\}$.