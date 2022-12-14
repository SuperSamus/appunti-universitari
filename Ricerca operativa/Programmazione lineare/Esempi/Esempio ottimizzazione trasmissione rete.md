# Esempio [[Problemi di ottimizzazione|ottimizzazione]] trasmissione rete

Dati:
- Rete descritta da [[Ottimizzazione grafi|grafo]] $G=(N,A)$, con linee $(i,j)∈A$
- $u_{ij}∈ℕ$ capacità di trasmissione per la linea (in numero di pacchetti)
- $c_{ij}>0$ prezzo della linea
- $p∈ℕ$ pacchetti da inviare dalla sorgente $s∈N$ alla destinazione $t∈N$

Quali linee affittare e come inviare i pacchetti utilizzando le linee affittate, per minimizzare il costo?

Da trovare:
- $x_{ij}∈ℕ$ numero di pacchetti che facciamo attraversare su $(i,j)$
- $y_{ij}=\begin{cases} 1 &\text{se si affitta la linea } (i,j)∈A \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Vincoli di capacità: $x_{ij}≤y_{ij}u_{ij} \quad (i,j)∈A$
- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = \begin{cases} -p &\text{se } i=s \\ p &\text{se } i=t \\ 0 &\text{altrimenti} \end{cases} \quad i ∈ N$

Funzione obiettivo: $\min ∑\limits_{(i,j)∈A}y_{ij}c_{ij}$
