### Proprietà dei nodi

**Degree**: numeri di archi connessi al nodo
**Degree centrality**: rapporto tra archi connessi in quel nodo e numero di archi in tutto il grafo
**Diametro**:
- Nodi $u$ e $v$: il numero di archi nel cammino minimo tra $u$ e $v$
- Grafo: il diametro più grande tra tutte le coppie di nodi
**Betweenness centrality**: rapporto dei cammini minimi che attraversano il nodo
**Closeness centrality**: distanza media del nodo rispetto agli altri nodi del grafo
**Eigenvector centrality**: l'importanza di un nodo dipende dall'importanza dei nodi vicini (definizione ricorsiva)
**Coefficiente di clustering**: scelto un nodo, prendi l'insieme dei suoi nodi adiacenti (sarà grande $n$): calcola il rapporto tra archi presenti nell'insieme e $n⋅(n-1)$ (il numero di archi che potrebbero esistere)
Per un grafo, più definizioni:
- Il coefficiente medio in tutti i nodi
- Rapporto tra triplette chiuse e quante ce ne potrebbero essere $\binom{n}{3}$

### Tipi di grafo

**Random** $(n,p)$: Per ogni coppia di nodi (ci sono $n$ nodi, quindi $\binom{n}{2}$ coppie), la loro probabilità di avere un arco è $p$
- Modello di Erdos e Renyi
- Diametro basso
- Coefficiente di clustering basso
- Non forma comunità
**Perfettamente regolare** ($n,k$): "Anello" dove ogni nodo è connesso a quelli adiacenti, fino a distanza $k$
- Diametro altissimo $⌈\frac{n}{k}⌉$
- Ci vuole più caos...
**Regolare** ($n,k,p$): Come quello regolare, ma ogni arco ha una probabilità $p$ di puntare a un altro nodo a caso
- Modello di Watts e Strogatz
- Diametro basso (anche con $p$ basso)
- Non forma comunità
- Implica numero fisso di nodi, non si può far crescere
**Barabasi-Albert** ($n,k$): aggiungi i nodi uno a uno, a collega ogni nuovo nodo a $k$ altri nodi, preferibilmente quelli che hanno un degree alto

Una rete è detta *scale free* se sono descritti dalla *power law*:
$$f(bx)=b^kf(x)$$