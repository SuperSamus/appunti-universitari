# Esercizi [[ricorsione]]

Definire $fact$ sia con $Y$ che $\Theta$:

### Mult (con $add$)

$mult \: n \: m =_\beta mult' \: n \: m$

$\Theta \: mult' = \Theta(\lambda f. \lambda n.\lambda m. ife(m==0,0,add \: n(f \: n (pred \: m))))$

### Fact

$\Theta fact$=\Theta(\lambda f.\lambda n.ife(n==0,1,f))

### Exp (anche direttamente)

### Pred

## Liste

Nel linguaggio $e::=...|nil|e::e|...$, una lista si rappresenta per esempio come $1::(2::(3::nil))$.

$nil$ e $cons$ sono definiti come:
- $nil \stackrel{\Delta}{=}\lambda x.\lambda y.y$
- $cons\stackrel{\Delta}{=}\lambda h.\lambda t.\lambda x.\lambda y.ht$

Definire le funzioni:
- $ADDLIST [n_1...n_k]=\displaystyle\sum_{i=1}^kn_i$
- $PRODLIST[n_1...n_k]=\displaystyle\prod_{i=1}^kn_i$
- $COMP \:f \: g=_\beta f \circ g$
- $MAP$
	- Ricorda che $MAP \: f(MAP \: g \: l)=_\beta MAP(f \circ g)l$