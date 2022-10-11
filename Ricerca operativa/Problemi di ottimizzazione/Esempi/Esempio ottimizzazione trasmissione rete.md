# Esempio [[Problemi di ottimizzazione|ottimizzazione]] trasmissione rete

Dati:
- Rete descritta da grafo $G=(N,A)$, con linee $(i,j)∈A$
- $u_{ij}$ capacità di trasmissione per la linea (in numero di pacchetti)
- $c_{ij}$ prezzo della linea
- $p$ pacchetti da inviare dalla sorgente $s∈N$ alla destinazione $t∈N$

Quali linee affittare e come inviare i pacchetti utilizzando le linee affittate, per minimizzare il costo?

Da trovare:
- $x_{ij}=\begin{cases} 1 &\text{se si affitta la linea } (i,j)∈A \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:


Funzione obiettivo min: $∑\limits_{(i,j)∈A}x_{ij}c_{ij}$
