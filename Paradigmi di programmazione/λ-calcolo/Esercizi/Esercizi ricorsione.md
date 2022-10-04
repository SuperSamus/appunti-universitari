# Esercizi [[ricorsione]]

Definire le seguenti operazioni sia con $Y$ che $\Theta$:

### \underline{mult} (con $\underline{add}$)

$\underline{mult} \: n \: m =_\beta \underline{mult}' \: n \: m$

$\Theta \: \underline{mult'} = \Theta(\lambda f. \lambda n.\lambda m. \underline{ite} \: (\underline{eq} \: m \: \underline{0}) \: 0 \: (\underline{add} \: n(f \: n (\underline{pred} \: m))))$

### Fact

$\Theta fact=\Theta(\lambda f.\lambda n.\underline{ite} \: (\underline{eq} \: n \: \underline{0}) \: 1 \: (\underline{mult} \: n (f (\underline{pred} \: n))))$

### Exp (anche direttamente)

$$
exp=\lambda n.\lambda m.\lambda f.\lambda x.m(\underline{mult} \: n)1 \\
=\lambda n.\lambda m.\lambda f.\lambda x.m((\lambda n.\lambda m.\lambda f.n(mf))n)(\lambda f.\lambda x.fx) \\
\rightarrow_\beta \lambda n.\lambda m.\lambda f.\lambda x.m(\lambda m.\lambda f.n(mf))(\lambda f.\lambda x.fx)
$$

$\Theta exp'=\Theta(\lambda f. \lambda n.\lambda m. \underline{ite} \: (\underline{eq} \: m \: \underline{0}) \: 1 \: (\underline{mult} \: n(f \: n (\underline{pred} \: m))))$

### Pred

$\Theta \underline{pred}=\Theta(\lambda f. \lambda s. \lambda n. \underline{ite} \: (\underline{eq} \: (\underline{succ} \: s) \: n)s(f(\underline{succ} \: s)n))0$

## Liste

Nel linguaggio $e::=...|nil|e::e|...$, una lista si rappresenta per esempio come $1::(2::(3::nil))$.

$a := [1, 2, 3] = λcn.c 1 (c 2 (c 3 n))$

Le operazioni base $nil$ (costruisci una lista vuota) e $cons$ (aggiungi un valore a inizio lista) sono definite come:
- $nil \stackrel{\Delta}{=}\lambda x.\lambda y.y$
- $cons\stackrel{\Delta}{=}\lambda h.\lambda t.\lambda x.\lambda y.ht$

Definire le funzioni:
- $\underline{add}LIST [n_1...n_k]=\displaystyle\sum_{i=1}^kn_i$
	- $\underline{add}LIST=\lambda l.l(\underline{mult})0=\lambda l.l(\lambda n. \lambda m. \lambda f. \lambda x. nf(mfx))(\lambda f.\lambda x.x)$
- $PRODLIST[n_1...n_k]=\displaystyle\prod_{i=1}^kn_i$
	- $PRODLIST=\lambda l.l(\underline{mult})1=\lambda l.l(\lambda n. \lambda m. \lambda f.n(mf)(\lambda f.\lambda x.fx)$
- $MAP$
	- Ricorda che $MAP \: f(MAP \: g \: l)=_\beta MAP(f \circ g)l$
	- $MAP=\lambda f.\lambda l.\lambda c.l(cf)$