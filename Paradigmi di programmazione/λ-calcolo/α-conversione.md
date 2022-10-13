# α-conversione

Forma di equivalenza del [[λ-calcolo]].

Formalmente, la relazione $=_α ⊆ Λ ⨉ λ$

$$
\cfrac{}{λx.t =_α λy.t[y/x]} \quad (x ∉ FV(t))
$$

$$
\cfrac{}{t=_α t} \text{ riflessiva} \quad \cfrac{t=_α s}{s=_α t} \text{ simmetrica} \quad \cfrac{t=_α s \quad s=_α u}{t=_α u} \text{ transitiva}
$$

$$
\cfrac{t=_α t' \quad s=_α s'}{ts=_α t's'} \quad \cfrac{t=_α s}{λx.t=_α λx.s}
$$

## Esempi

- `function succ(x) {x+1}` $=_α$ `function succ(y) {y+1}`
- $\lim\limits_{x \to +∈fty} e^{-x}=_α \lim\limits_{y \to +∈fty} e^{-y}$
- $λxy.x(xy)=_α λab.a(ab)$
	- $λy.x(xy) =_α λb.x(xb)$
	- $⇒ λx.λy.x(xy)=_α λx.λb.x(xb) =_α λa.λb.a(ab)$

## Lemma

$$
\cfrac{t =_α t' \quad s=_α s'}{t[s/x]=_α t'[s'/x]}
$$

## NB

Ogni volta che definiamo un'operazione sul λ-calcolo (come sostituzione, ottimizzazione…), bisogno dimostrare che l'operazione è invariante per l'α-equivalenza (non dipende dalla scelta dei nomi dei parametri formali.)

$F: Λ^n → Λ$

$t_1=_α s_1,…, t_n =_α s_n ⇒ F(t_1,…,t_n)=_α F(s_1,…,s_n)$