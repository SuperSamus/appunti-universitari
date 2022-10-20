# Esercizi [[ricorsione]]

Definire le seguenti operazioni ricorsivamente:

### Mult (con $\underline{add}$)

$\underline{mult} \: n \: m =_β \underline{mult}' \: n \: m$

$\underline{mult'}≜Θ(λf.λn.λm.\underline{ite} \: (\underline{eq} \: m \: \underline{0}) \: 0 \: (\underline{add} \: n(f \: n (\underline{pred} \: m))))$

### Fact

$\underline{fact}≜Θ(λf.λn.\underline{ite} \: (\underline{eq} \: n \: \underline{0}) \: 1 \: (\underline{mult} \: n (f (\underline{pred} \: n))))$

### Exp (anche direttamente)

$$
\underline{exp}≜λn.λm.λf.λx.m(\underline{mult} \: n)1 \\
=λn.λm.λf.λx.m((λn.λm.λf.n(mf))n)(λf.λx.fx) \\
→_β λn.λm.λf.λx.m(λm.λf.n(mf))(λf.λx.fx)
$$

$\underline{exp'}≜Θ(λf.λn.λm.\underline{ite} \: (\underline{eq} \: m \: \underline{0}) \: 1 \: (\underline{mult} \: n(f \: n (\underline{pred} \: m))))$

### Pred

$\underline{pred}≜Θ(λf.λs.λn.\underline{ite} \: (\underline{eq} \: (\underline{succ} \: s) \: n)s(f(\underline{succ} \: s)n))0$

## Liste

Nel linguaggio $e::=...|nil|e::e|...$, una lista si rappresenta per esempio come $1::(2::(3::nil))$.

$a := [1, 2, 3] = λcn.c 1 (c 2 (c 3 n))$

Le operazioni base $\underline{nil}$ (costruisci una lista vuota) e $\underline{cons}$ (aggiungi un valore a inizio lista) sono definite come:
- $\underline{nil} ≜λx.λy.y$
- $\underline{cons} ≜λh.λt.λx.λy.ht$

Definire le funzioni:
- $ADDLIST [n_1...n_k]≜∑\limits_{i=1}^kn_i$
	- $\underline{ADDLIST}≜λl.l(\underline{mult})0=λl.l(λn.λm.λf.λx.nf(mfx))(λf.λx.x)$
- $PRODLIST[n_1...n_k]≜∏\limits_{i=1}^kn_i$
	- $\underline{PRODLIST}≜λl.l(\underline{mult})1=λl.l(λn.λm.λf.n(mf)(λf.λx.fx)$
- $MAP$
	- Ricorda che $\underline{MAP} \: f(\underline{MAP} \: g \: l)=_β \underline{MAP}(f ∘ g)l$
	- $\underline{MAP}≜λf.λl.λc.l(cf)$