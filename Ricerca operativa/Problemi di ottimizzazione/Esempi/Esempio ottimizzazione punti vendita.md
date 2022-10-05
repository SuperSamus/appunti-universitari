# Esempio [[Problemi di ottimizzazione|ottimizzazione]] punti vendita

La direzione marketing di un'azienda decide di aprire al più $m$ magazzini per servire $n$ punti vendita. La direzione deve stabilire anche la capacità di ogni magazzino aperto, che può essere scelta nell'insieme $\{u_1, u_2, u_3\}$.
Il costo $c_{hj}$ di apertura del magazzino $j$ dipende dalla capacità $u_h$ scelta.
Sapendo che il punto vendita $i$ ha domanda $d_i$, si formuli in termini di Programmazione Lineare Intera il problema di stabilire quali magazzini aprire e le relative capacità, ed assegnare gli $n$ punti vendita ai magazzini
aperti, in modo da rispettare le capacità e minimizzando il costo totale di attivazione (suggerimento: la decisione di non aprire un magazzino può essere espressa assegnandogli capacità zero).

Da trovare:
- $s_{ij} ∈ \{0,1\}$ se il punto vendita $i$ compra dal magazzino $j$
- $h_{kj} ∈ \{0,1\}$ se il magazzino $j$ sceglie la capacità $k=1…3$

Vincoli:
- Ogni negozio sceglie un magazzino: $\displaystyle∑_{j=1}^m s_{ij}=1   i=1...n$
- Ogni magazzino sceglie al massimo una capacità: $\displaystyle∑_{h=1}^3 k_{hj} ≤ 1   j=1…m$
- Ogni magazzino ha abbastanza capacità per tutti i negozi: $\displaystyle∑_{h=1}^3 u_hk_{hj} ≥ ∑_{i=1}^n d_is_{ij}   j=1…m$

Funzione obiettivo min: $\displaystyle∑_{j=1}^m∑_{h=1}^3 c_{hj}$