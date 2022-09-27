# Sostituzioni

Cosa vuol dire $t[s/x]$?

È il termine ottenuto sostituendo tutte le occorrenze *libere* di $x$ in $t$ con $s$.

- $x[s/x]=s$
- $y[s/x]=y \quad (y \neq x)$
- $(tu)[s/x]=t[s/x]u[s/x]$
- $(\lambda x.t)[s/x]=\lambda x.t$
- $(\lambda y.t)[s/x]=\lambda y.t[s/x]$

## Problema

Questo *non* è vero: $\lambda x.t \equiv \lambda y.t[y/x]$

Esempio: $(\lambda x.y)[x/y]=\lambda x.x$

Non dobbiamo consentire alla funzione di catturare variabili.

## Due casi

- $(\lambda x.t)[s/x]= \lambda x.t$
- $(\lambda y.t)[s/x]=\lambda y.t[s/x] \quad (\text{se } y \not \in FV(s))$
- $(\lambda y.t)[s/x]=(\lambda z.t[z/y])[s/x]=\lambda z.t[z/y][s/x] \quad (\text{se } z \not \in FV(t) \land z \not \in FV(s))$

## Esercizi

[[Esercizi sostituzioni]]