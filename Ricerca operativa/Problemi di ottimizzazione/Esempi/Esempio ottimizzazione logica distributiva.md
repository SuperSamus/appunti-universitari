# Esempio ottimizzazione logica distributiva

Il Ministro dell'Energia ha $m$ depositi di riserve di gas acquistate per rifornire $n$ regioni. Ciascuna regione $i$ dovrà attingere a $b_i$ milioni di $m^3$ da queste riserve, mentre ogni deposito $j$ ne contiene $u_j$. Ogni regione viene rifornita da un unico deposito. Il costo di spedizione sostenuto dal deposito $j$ verso la regione $i$ è $c_{ij}$ euro per milioni di $m^3$. Se il deposito rifornisce almeno una regione serve un costo fisso $c_j$ per la gestione.
Soddisfa le necessità minimizzando il costo.

Variabili extra:
- $x_{ij} \in \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se la regione } i \text{ viene rifornita dal deposito } j \\ 0 &\text{altrimenti} \end{cases}$
- $y_j \in \{0,1\} \quad y_j=\begin{cases} 1 &\text{se il deposito } j \text{ rifornisce almeno una regione} \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Vincoli di capacità: $\displaystyle\sum_{j=1}^m b_ix_{ij} \leq u_jy_j \quad i=1...n$
	- Inoltre, se il deposito non viene usato, non ha capacità.
- Vincoli di semiassegnamento: $\displaystyle\sum_{j=1}^m x_{ij}=1 \quad i=1...n$
Funzione obiettivo min: $- $\displaystyle\sum_{j=1}^m \displaystyle\sum_{i=1}^n c_{ij}b_ix_{ij}+\frac{c_jy_j}{n}$