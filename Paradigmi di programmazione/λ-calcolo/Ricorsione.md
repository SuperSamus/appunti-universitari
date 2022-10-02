# Ricorsione

## Definizione

In un linguaggio $e::=z|succ(e)$, il principio di induzione per una funzione $F:Exp \rightarrow \mathbb{N}$ si definisce come $\forall e. P(e) \Leftarrow P(z) \land \forall x.P(x) \rightarrow P(succ(x))$

In modo simile, si può costruire una funzione $\varphi: P(u) \rightarrow P(u)$[^1], definita come $\varphi(A)=\{z\} \cup \{succ(a)|a \in A\} \cup A$. Per esempio:
- $\varphi(\emptyset)=\{z\}$
- $\varphi(\varphi(\emptyset))=\{z, succ(z)\}$
- $\varphi(\varphi(\varphi(\emptyset)))=\{z, succ(z), succ(succ(z))\}$



## Punto fisso

Data una funzione $F:A \rightarrow A$ , un punto fisso $x \in A$ della funzione $F$ ha la proprietà che $f(x)=x$.

Teorema: ogni λ-termine ha un punto fisso: $ta=_\beta a$

Dimostrazione: sia $F$ una funzione, e $H=\lambda x.F(xx)$. Allora $HH=_\beta F(HH)$, quindi $HH$ è un punto fisso di $F$.

Ciò implica che il λ-calcolo non si può usare per implementare la *logica*, in quanto richiede che certe funzionalità (come le negazione logica) *non* abbiano alcun punto fisso.

[^1]: Sarebbero l'insieme delle parti (l'insieme di tutti i sottoinsiemi) dell'universo