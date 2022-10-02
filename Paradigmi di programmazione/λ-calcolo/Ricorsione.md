# Ricorsione

## Definizione

In un linguaggio $e::=0|succ(e)$

Per esempio: $F=\lambda n.ife(Eq \: n \: 0,1,mul \: F(pred \: n))$

## Punto fisso

Data una funzione $F:A \rightarrow A$ , un punto fisso $x \in A$ della funzione $F$ ha la proprietà che $f(x)=x$.

Teorema: ogni λ-termine ha un punto fisso: $ta=_\beta a$

Dimostrazione: sia $F$ una funzione, e $H=\lambda x.F(xx)$. Allora $HH=_\beta F(HH)$, quindi $HH$ è un punto fisso di $F$.

Ciò implica che il λ-calcolo non si può usare per implementare la *logica*, in quanto richiede che certe funzionalità (come le negazione logica) *non* abbiano alcun punto fisso.