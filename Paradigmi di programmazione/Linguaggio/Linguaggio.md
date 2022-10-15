# Linguaggio

## Sintassi

$E∋e::=x|\underline{n}|\underline{b}|\textquotedblleft s \textquotedblright|e+e|e*e|e\textasciicircum e|ite(e,e,e)|\text{let }x=e \text{ in }e|λx.e|ee$

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

## Semantica

$t,s::=x|\underline{n}|\underline{b}|succ \: t|pred \: t|ite(t,t,t)|\text{let }x=e \text{ in }e$

$v,w::=x|\underline{n}|\underline{b}$

$$
\cfrac{t→t'}{ite(t,s,u)→ite(t',s,y)} \quad
\cfrac{}{ite(true,t,s)→t} \quad
\cfrac{}{ite(false,t,s)→s}
$$

$$
\cfrac{t→t'}{\text{let }x=t \text{ in }s→\text{let }x=t' \text{ in } s} \quad
\cfrac{}{\text{let }x=v \text{ in }s→s[v/x]}
$$

$$
\cfrac{}{succ \: \underline{n}→\underline{n+1}}
$$