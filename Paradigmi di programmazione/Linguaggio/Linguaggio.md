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

Con la sintassi:
- $t,s::=x|\underline{n}|\underline{b}|succ \: t|pred \: t|ite(t,t,t)|\text{let }x=e \text{ in }e$
- $v,w::=x|\underline{n}|\underline{b}$

La riduzione porta un termine a un altro termine. $→⊆t×t$

È deterministica. $\begin{matrix} t→s_1 \\ t→s_2 \end{matrix} ⇒ s_1 =_α s_2$

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
\cfrac{}{prec \: \underline{n}→\underline{n-1}} \quad
\cfrac{}{succ \: \underline{n}→\underline{n+1}}
$$

### Esempio

$pred(succ \: \underline{0})$
$$
\cfrac{\cfrac{}{succ \: \underline{0}→\underline{1}}}{pred(succ \: \underline{0})→pred(\underline{1})} \quad
\cfrac{}{prec \: \underline{1}→0}
$$

## Unione disgiunta funzioni

$$
\begin{matrix} f:A→B \\ g:A'→B' \end{matrix} \quad A∩A'=∅ \quad f+g:A∪A'→B∪B' \quad (f+g)(x)≜\begin{cases} f(x) & \text{se } x∈A \\ g(x) & \text{se } x∈A' \end{cases}
$$

Utile quando si ha due ambienti diversi:

$$
(Γ+Δ)(x)≜\begin{cases} Γ(x) & \text{se } x∈A \\ Δ(x) & \text{se } x∈A' \end{cases}
$$