# Esempio [[Problemi di ottimizzazione|ottimizzazione]] logica distributiva

Il Ministro dell'Energia ha $m$ depositi di riserve di gas acquistate per rifornire $n$ regioni. Ciascuna regione $i$ dovrà attingere a $b_i$ milioni di m³ da queste riserve, mentre ogni deposito $j$ ne contiene $u_j$. Ogni regione viene rifornita da un unico deposito. Il costo di spedizione sostenuto dal deposito $j$ verso la regione $i$ è $c_{ij}$ euro per milioni di m³. Se il deposito rifornisce almeno una regione serve un costo fisso $f_j$ per la gestione.
Soddisfa le necessità minimizzando il costo.

Variabili extra:
- $x_{ij} ∈ \{0,1\} \quad x_{ij}=\begin{cases} 1 &\text{se la regione } i \text{ viene rifornita dal deposito } j \\ 0 &\text{altrimenti} \end{cases}$
- $y_j ∈ \{0,1\} \quad y_j=\begin{cases} 1 &\text{se il deposito } j \text{ rifornisce almeno una regione} \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Vincoli di capacità: $∑\limits_{j=1}^m b_ix_{ij} ≤ u_jy_j \quad i=1…n$
	- Inoltre, se il deposito non viene usato, non ha capacità.
- Vincoli di semiassegnamento: $∑\limits_{j=1}^m x_{ij}=1 \quad i=1…n$

Funzione obiettivo: $\min ∑\limits_{j=1}^m (f_jy_j + ∑\limits_{i=1}^n c_{ij}b_ix_{ij})$

## Variante

La stessa regione ora può essere rifornita da quanti depositi vuole.

Si rifà tutto!

Da trovare:
- $x_{ij} ∈ ℝ_{≥ 0}$ quanto gas prende la regione $i$ dal deposito $j$
- $y_j ∈ \{0,1\} \quad y_j=\begin{cases} 1 &\text{se il deposito } j \text{ rifornisce almeno una regione} \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Vincoli di capacità: $∑\limits_{i=1}^n x_{ij} ≤ u_jy_j \quad j=1…m$
- Vincoli di domanda: $∑\limits_{j=1}^m x_{ij}=b_i \quad i=1…n$

Funzione obiettivo: $\min ∑\limits_{j=1}^m (f_jy_j + ∑\limits_{i=1}^n c_{ij}s_{ij})$
