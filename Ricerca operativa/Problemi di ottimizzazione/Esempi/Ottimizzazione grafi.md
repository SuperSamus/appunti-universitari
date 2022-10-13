# Grafi

In un [[Problemi di ottimizzazione|problema di ottimizzazione]] di un grafo $G=(N,A)$, con archi $(i,j)∈A$, descrivendo $x_{ij}$ come il flusso nell'arco $(i,j)$ e $b_i$ come il bilancio del nodo $i$, generalmente si ha questo vincolo:

- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = b_i \quad i ∈ N$
	- Stella entrante: $BN(i)=\{j ∈ N : (j,i) ∈ A\}$
	- Stella uscente: $FN(i)=\{j ∈ N : (i,j) ∈ A\}$

$b_i$ può essere positivo o negativo per scegliere a piacere tra *pozzo* o *sorgente*.

## Cammino minimo

Abbiamo una sorgente $s∈N$ e una destinazione $t∈N$ a cui dobbiamo trasmettere un singolo elemento, gli archi che hanno un costo $c_{ij}$.

Da qui si può rappresentare un problema di cammino minimo con $b_s=-1$, $b_t=1$ (o viceversa) e tutti gli altri $b_i=0$, possiamo rappresentare un  con:

Funzione obiettivo min: $∑\limits_{(i,j)∈A}x_{ij}c_{ij}$