# Esempio [[Problemi di ottimizzazione|ottimizzazione]] acqua

I numeri tra parentesi sono la quantità d'acqua che viene prodotta in quel nodo, identificato dal numero fuori dalla parentesi.

Tutta questa acqua deve essere mandata nel depuratore (a destra), minimizzando i costi (mostrati negli archi, per unità d'acqua).

Per esempio:

```mermaid
flowchart LR
2["2(3)"] -- 2 --> 1
5["5(2)"] -- 1 --> 1
4["4(1)"] -- 6 --> 1
4 -- 4 --> 5
3["3(2)"] -- 4 --> 2
3 -- 2 --> 4
```
Dati:
- $A$ archi
- $b_i$ quantità d'acqua prodotta dal nodo $i∈A$

Da trovare:
- $x_{ij}$ m³ acqua che transitano attraverso $(i,j)$

Problemi nel creare i vincoli:
- L'acqua deve tutta andare al depuratore:
	- Non il modo migliore per implementarlo: $x_{21}+x_{41}+x_{51}=8$
	- E il nodo 3? Deve passare per più nodi, ciò rende le cose difficili.
		- $x_{34}+1=x_{41}+x_{45}$
	- Come si generalizza?

Vincoli:
- $∑\limits_{j∈BN(i)} x_{ji} + b_i=∑\limits_{j∈FN(i)} x_{ij} \quad i ∈ N$
	- Stella entrante: $BN(i)=\{j ∈ N : (j,i) ∈ A\}$
	- Stella uscente: $FN(i)=\{j ∈ N : (i,j) ∈ A\}$

TODO

Funzione obiettivo min: $∑\limits_{i,j ∈ A} c_{ij}x_{ij}$
