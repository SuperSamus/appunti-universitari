# Linguaggio

## Sintassi $E∋e::=x|\underline{n}|\textquotedblleft s \textquotedblright|true|false|e+e|e*e|e\textasciicircum e|ite(e,e,e)|\text{let }x=e \text{ in }e|λx.e|ee$

$P=\{e∈E|FV(e)=∅\}$

$e=_αe'$

$$
\text{let }x=e \text{ in }e' \\
=_α \\
\text{let }y=e \text{ in }e'[y/x] \quad y ∉ FV(e')
$$

Esempi di programmi:

```
let x = 3+2 in
let y = 5+2 in
x+y
```

## Regole

$$
\cfrac{t→t'}{ite(t,s,u)→ite(t',s,y)} \quad
\cfrac{t→t'}{\text{let }x=t \text{ in }(t,s,u)→ite(t',s,y)} \quad
$$