# Generalizzazione [[Problemi di ottimizzazione|ottimizzazione]] flussi

Dati:
- $A$ archi
- $b_i$ bilancio del nodo $i$
	- Positivo: pozzo, esce meno di quello che entra
	- Negativo: sorgente, esce più di quello che entra
- $u_{ij}$ capacità arco

Da trovare:
- $x_{ij}$ quantità che transita attraverso $(i,j)∈A$

Vincoli:
- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = b_i \quad i ∈ N$
	- Stella entrante: $BN(i)=\{j ∈ N : (j,i) ∈ A\}$
	- Stella uscente: $FN(i)=\{j ∈ N : (i,j) ∈ A\}$
- Bilanci nodi: $∑\limits_{i∈N}b_i=0$
- Vincoli di capacità $0≤x_{ij}≤u_{ij} \quad (i,j)∈A$

Funzione obiettivo min: $∑\limits_{(i,j) ∈ A} c_{ij}x_{ij}$
