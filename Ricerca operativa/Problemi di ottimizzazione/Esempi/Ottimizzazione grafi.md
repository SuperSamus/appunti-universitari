# Grafi

Un [[Problemi di ottimizzazione|problema di ottimizzazione]] di grafo $G=(N,A)$, con archi $(i,j)∈A$, descrivendo $x_{ij}$ come il flusso nell'arco $(i,j)$ e $b_i$ come il bilancio del nodo $i$ generalmente ha questi vincoli:

Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = b_i \quad i ∈ N$