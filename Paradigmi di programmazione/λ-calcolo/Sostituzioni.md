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

- $(λy.t)[s/x]=λy.t[s/x] \quad (\text{se } y ∉ FV(s))$
- $(λy.t)[s/x]=(λz.t[z/y])[s/x]=λz.t[z/y][s/x] \quad (\text{se } z ∉ FV(t) ∧ z ∉ FV(s))$

## Strategie di valutazione

$(λx.x^2+2x+3)(2+3))$

- Chiamata per nome (CbN): rimpiazza $x$ con $2+3$
	- $→_β t[s/x]$
- Chiamata per valore (CbV): valuta $2+3$, e rimpiazza $x$ con il risultato
	- $→^*(λx.t)v →_β t[v/x]$

### Teoremi

Ci sono $t↓_{CbN}$ ($t$ termina) e $t↑_{CbV}$ ($t$ non termina).
- $KIΩ ≜ (λx.λy.x)IΩ$
	- CbV: $KIΩ$
	- CbN: $(λy.I)Ω$
		- CbV: $(λy.I)Ω$
		- CbN: $I$

Non vale viceversa. Teorema: se $t→_β^* s \not →_β$ allora $t \xrightarrow{CbN}_β^* s$

CbV però è più efficiente.

Call-by-Need (lazy): inizialmente CbN, ma valuta il valore appena serve valutarlo. Utile per qualsiasi cosa infinita (come gli iteratori), dato che evita calcoli inutili.

CbN e Call-by-Need si comportano in maniera imprevedibile (o indesiderabile) con gli effetti collaterali. Se li si vuole avere, CbV è l'unica scelta sensata.

### Definizione formale

$(λx.t)s \xrightarrow{CbV}_β t[s/x] \quad (\text{se } s \not \xrightarrow{CbV}_β)$

$$
\frac{t \xrightarrow{CbV}_β s}{λx.t \xrightarrow{CbV}_β λx.s}
$$
$$
\frac{t \xrightarrow{CbV}_β t'}{ts \xrightarrow{CbV}_β t's} \quad
\frac{s \xrightarrow{CbV}_β s' \quad t \not \xrightarrow{CbV}_β}{ts \xrightarrow{CbV}_β ts'}
$$
Per esempio, dati:
- $K ≜ λx.λy.x$
- $M ≜ K(II)((λx.xx)(λy.yz)u)$
- $N ≜ (λx.xx)(λy.yz)u$

$$
M=(KII)N \\
\xrightarrow{CbV}_β(KI)N \\
\xrightarrow{CbV}_β(λy.I)N \\
=(λy.I)((λx.xx)((λy.yz)u)) \\
\xrightarrow{CbV}_β (λy.I)((λx.xx)(uz)) \\
\xrightarrow{CbV}_β ((λy.I)(uz))(uz) \\
\xrightarrow{CbV}_β I(uz) \\
\xrightarrow{CbV}_β uz
$$
