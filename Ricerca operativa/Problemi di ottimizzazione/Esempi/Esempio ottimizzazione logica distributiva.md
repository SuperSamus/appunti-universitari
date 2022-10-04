# Esempio ottimizzazione logica distributiva

Il Ministro dell'Energia ha $m$ depositi di riserve di gas acquistate per rifornire $n$ regioni. Ciascuna regione $i$ dovrà attingere a $b_i$ milioni di $m^3$ da queste riserve, mentre ogni deposito $j$ ne contiene $u_j$. Ogni regione viene rifornita da un unico deposito ($d_{ij}$). Il costo di spedizione sostenuto dal deposito $j$ verso la regione $i$ è $c_{ij}$ euro per milioni di $m^3$. Se il deposito rifornisce almeno una regione ($x_j$) serve un costo fisso $c_j$ per la gestione.
Soddisfa le necessità minimizzando il costo.

Variabili extra:
- $d_{ij} \in \{0,1\} \quad d_{ij}=\begin{cases} 1 &\text{se la regione } i \text{ viene rifornita dal deposito } j \\ 0 &\text{altrimenti} \end{cases}$
- 

Vincoli:
- $\displaystyle\sum_{i=1}^n (d_{ij}b_i) \leq u_j \quad j=1...m$
- 