# Esercizi [[ricorsione]]

Definire $fact$ sia con $Y$ che $\Theta$:

### Mult (con $add$)

$mult \: n \: m =_\beta mult' \: n \: m$

$\Theta \: mult' = \Theta(\lambda f. \lambda n.\lambda m. ife \: m==0 \: 0 \: (add \: n(f \: n (pred \: m))))$

### Fact

$\Theta fact=\Theta(\lambda f.\lambda n.ife \: n==0 \: 1 \: (mult \: n (f (pred \: n))))$

### Exp (anche direttamente)

$$
exp=\lambda n.\lambda m.\lambda f.\lambda x.m(mult \: n)1 \\
=\lambda n.\lambda m.\lambda f.\lambda x.m((\lambda n.\lambda m.\lambda f.n(mf))n)(\lambda f.\lambda x.fx) \\
\rightarrow_\beta \lambda n.\lambda m.\lambda f.\lambda x.m(\lambda m.\lambda f.n(mf))(\lambda f.\lambda x.fx)
$$

$\Theta exp=\Theta(\lambda f. \lambda n.\lambda m. ife \: m==0,1 \: (mult \: n(f \: n (pred \: m))))$

### Pred

$\Theta pred=\Theta(\lambda f. \lambda s. \lambda n. ife \: ((succ \: s)==n)s(f(succ \: s)n))0$

## Liste

Nel linguaggio $e::=...|nil|e::e|...$, una lista si rappresenta per esempio come $1::(2::(3::nil))$.

Le operazioni base $nil$ (costruisci una lista vuota) e $cons$ (aggiungi un valore a inizio lista) sono definite come:
- $nil \stackrel{\Delta}{=}\lambda x.\lambda y.y$
- $cons\stackrel{\Delta}{=}\lambda h.\lambda t.\lambda x.\lambda y.ht$

Definire le funzioni:
- $ADDLIST [n_1...n_k]=\displaystyle\sum_{i=1}^kn_i$
- $PRODLIST[n_1...n_k]=\displaystyle\prod_{i=1}^kn_i$
- $COMP \:f \: g=_\beta f \circ g$
- $MAP$
	- Ricorda che $MAP \: f(MAP \: g \: l)=_\beta MAP(f \circ g)l$