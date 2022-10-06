# Esempio [[Problemi di ottimizzazione|ottimizzazione]] supermercati

Siamo una catena si supermercati che vuole entrare nel mercato della Toscana aprire un certo numero di punti vendita. La catena ha individuato un certo numero di siti potenziali, e tu deciderai in quali di questi siti li costruirai.

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
	- Con $≤$: vincolo di riempimento (obiettivo max)

Funzione obiettivo min: $∑\limits_{j=1}^m c_jx_j$

### Selezione di sottoinsiemi

- $N=\{1,…,n\}$
- $F_1,F_2,...,F_n⊆N$
- $c_1,c_2,...,c_n$ costo di selezione
- $a_{ij} ∈ \{0,1\} \quad a_{ij}=\begin{cases} 1 &\text{se } i ∈ F_j \\ 0 &\text{altrimenti} \end{cases}$

Problema di copertura: selezionare sottoinsiemi in modo che ciascun elemento di $N$ appartenga almeno ad uno dei sottoinsiemi selezionati, al minor costo possibile.

Da trovare:
- $x_j ∈ \{0,1\} \quad x_j=\begin{cases} 1 &\text{se selezioniamo } F_j \\ 0 &\text{altrimenti} \end{cases}$

VIncoli:
- Vincolo di copertura: $∑\limits_{j=1}^m a_{ij}x_j ≥ 1 \quad i ∈ N$
	- Con $=$: vincolo di partizione
	- Con $≤$: vincolo di riempimento (obiettivo max)


Funzione obiettivo min: $∑\limits_{j=1}^m c_jx_j$