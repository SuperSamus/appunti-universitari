# Esempio [[Problemi di ottimizzazione|ottimizzazione]] supermercati

Dati:
- $m$ siti potenziali per costruzione supermercati
- $c_j$ costo costruzione di un supermercato nella località $j$
- $n$ località da servire
- $d_{ij}$ distanza tra la località $i$ e il sito $j$
- $a_{ij} ∈ \{0,1\} \quad a_{ij}=\begin{cases} 1 &\text{se } d_{ij} ≤ 10 \\ 0 &\text{altrimenti} \end{cases}$
	- Il valore è fissato a creazione problema, non è un valore da trovare

Da trovare:
- $x_j ∈ \{0,1\} \quad x_j=\begin{cases} 1 &\text{se costruiamo il supermercato in } j \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Vincolo di copertura: $∑\limits_{j=1}^m a_{ij}x_j ≥ 1 \quad i=1…n$
	- Con $=$: vincolo di partizione
	- Con $≤$: vincolo di riempimento

Funzione obiettivo min: $∑\limits_{j=1}^m c_jx_j$
