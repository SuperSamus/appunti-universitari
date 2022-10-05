# Esempio [[Problemi di ottimizzazione|ottimizzazione]] supermercati
Dati:
- $m$ siti potenziali per costruzione supermercati
- $c_j$ costo costruzione di un supermercato nella località $j$
- $n$ località da servire
- $d_{ij}$ distanza tra la località $i$ e il sito $j$
- $a_{ij} ∈ \{0,1\} \quad a_{ij}=\begin{cases} 1 &\text{se } d_{ij} ≤ 10 \\ 0 &\text{altrimenti} \end{cases}$, variabile logica

Da trovare:
- $x_j ∈ \{0,1\}$ se costruiamo supermercato in $j$.

Funzione obiettivo: $∑\limits_{i=1}^m c_jx_j$