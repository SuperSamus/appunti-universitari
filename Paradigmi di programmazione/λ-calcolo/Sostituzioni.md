# Sostituzioni

Cosa vuol dire $t[s/x]$?

È il termine ottenuto sostituendo tutte le occorrenze *libere* di $x$ in $t$ con $s$.

- $x[s/x]=s$
- $y[s/x]=y \quad (y ≠ x)$
- $(tu)[s/x]=t[s/x]u[s/x]$
- $(λx.t)[s/x]=λx.t$
- $(λy.t)[s/x]=λy.t[s/x]$

## Problema

Questo *non* è vero: $λx.t =_α λy.t[y/x]$

Esempio: $(λx.y)[x/y]=λx.x$

Non dobbiamo consentire alla funzione di catturare variabili.

## Due casi

- $(λx.t)[s/x]= λx.t$
- $(λy.t)[s/x]=λy.t[s/x] \quad (\text{se } y \not ∈ FV(s))$
- $(λy.t)[s/x]=(λz.t[z/y])[s/x]=λz.t[z/y][s/x] \quad (\text{se } z \not ∈ FV(t) ∧ z \not ∈ FV(s))$
- 