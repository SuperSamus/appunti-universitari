# Ricorsione

## Problema

Come si può definire nel [[λ-calcolo]] una funzione che chiama se stessa?

In un linguaggio $e::=z|succ(e)$, il principio di induzione per una funzione $F:Exp \rightarrow \mathbb{N}$ si definisce come $\forall e. P(e) \Leftarrow P(z) \land \forall x.P(x) \rightarrow P(succ(x))$

In modo simile, si può costruire una funzione $\varphi: P(u) \rightarrow P(u)$[^1], definita come $\varphi(A)=\{z\} \cup \{succ(a)|a \in A\} \cup A$. Per esempio:
- $\varphi(\emptyset)=\{z\}$
- $\varphi(\varphi(\emptyset))=\{z, succ(z)\}$
- $\varphi(\varphi(\varphi(\emptyset)))=\{z, succ(z), succ(succ(z))\}$

Notevolmente:
- $\varphi(A)=A$
- $\varphi(Exp)=Exp$
	- $\varphi(B) \subseteq B \Rightarrow Exp \subseteq B$

## Punto fisso

Data una funzione $f:A \rightarrow A$ , un punto fisso $x \in A$ della funzione $f$ ha la proprietà che $f(x)=x$.

Teorema: ogni λ-termine ha un punto fisso: $\forall f \in \Lambda.\exists t \in \Lambda \quad ft=_\beta t$.[^2]

Dimostrazione: sia $f$ una funzione, e $H=\lambda x.f(xx)$. Allora $HH \rightarrow_\beta f((\lambda x.f(xx))(\lambda x.f(xx)))=_\beta f(HH)$, quindi $HH$ è un punto fisso di $f$.

## Fix

Questa cosa non si può fare: $t=_\beta\lambda n.\underline{ite} \: (\underline{eq} \: n \: \underline{0}) \: \underline{1} \: (\underline{mult} \: n(t(\underline{prec} \: n)))$

Però si può fare $s=\lambda f.\lambda n.\underline{ite} \: (\underline{eq} \: n \: \underline{0}) \: \underline{1} \: (\underline{mult} \: n(f(\underline{prec} \: n)))$

Da qui ci vorrebbe un λ-termine $fix$ tale che $fix \: t \rightarrow_\beta^\star t(fix \: t)$.

$fix \: s \rightarrow_\beta s(fix \: s) \rightarrow_\beta \lambda n.\underline{ite} \: (\underline{eq} \: n \: \underline{0}) \: \underline{1} \: (\underline{mult} \: n((fix \: s)(\underline{prec} \: n)))$

Eseguiamolo con 2:

$$
(fix \: s)2 \\
\rightarrow_\beta^\star \underline{ite} \: (\underline{eq} \: \underline{2} \: \underline{0}) \: \underline{1} \: (\underline{mult} \: n((fix \: s)(\underline{prec} \: \underline{2}))) \\
\rightarrow_\beta^\star \underline{mult} \: \underline{2}((fix \: s)\underline{1}) \\
\rightarrow_\beta^\star \underline{mult} \: \underline{2}(s(fix \: s)\underline{1}) \\
\rightarrow_\beta^\star \underline{mult} \: \underline{2}(\underline{mult} \: \underline{1}((fix \: s)\underline{0})) \\
\rightarrow_\beta^\star \underline{mult} \: \underline{2}(\underline{mult} \: \underline{1}(\underline{1})) \\
\rightarrow_\beta^\star \underline{2}
$$

Ora che tutto è definito, definiamo $F \: n=e[F]$[^3] come zucchero sintattico per $fix(\lambda f.\lambda n.e[f])$.

## Definizione Fix

Da $HH$$ si può creare il **combinatore Curry**: $Y \stackrel{\Delta}{=} \lambda f.(\lambda x.f(xx))(\lambda x.f(xx))$.

Con $\Delta_f \stackrel{\Delta}{=} \lambda x.f(xx)$

Da qui:
- $Yf \rightarrow_\beta (\lambda x.f(xx))(\lambda x.f(xx)) \rightarrow_\beta f((\lambda x.f(xx))(\lambda x.f(xx)))=f(\Delta_f\Delta_f)$
- $f(Yf) \rightarrow_\beta f((\lambda f.(\lambda x.f(xx))(\lambda x.f(xx)))f) \rightarrow_\beta f((\lambda x.f(xx))(\lambda x.f(xx)))=f(\Delta_f\Delta_f)$

Quindi $Yf =_\beta f(Yf)$. Tuttavia per $fix$ si cerca una β-riduzione, non una β-equivalenza. Proviamo un'altra cosa:
- $A=\lambda xy.y(xxy)$
- $\Theta=AA$
- $\Theta f=(\lambda xy.y(xxy))Af \rightarrow_\beta (\lambda y.y(AAy))f \rightarrow_\beta f(AAf)=f(\Theta f)$

Quindi $fix=\Theta$.

[^1]: Sarebbero l'insieme delle parti (l'insieme di tutti i sottoinsiemi) dell'universo
[^2]: Ciò implica che con il λ-calcolo non si può usare per implementare la *logica*, in quanto richiede che certe funzionalità (come le negazione logica) *non* abbiano alcun punto fisso.
[^3]: Vuol dire che $e$ utilizza $F$
