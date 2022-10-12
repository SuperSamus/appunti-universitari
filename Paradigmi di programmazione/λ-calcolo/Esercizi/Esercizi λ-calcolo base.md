# Esercizi [[λ-calcolo]] base

Determinare quali delle seguenti espressioni sono λ-termini:

- $λ$ NO
- $(λx)$ NO
- $λx.y$ SI
- $xxxx$ NO
- $λ(xy).x$ NO
- $x$ SI
- $y$ SI
- $xx$ SI
- $(λx.(x(λy)))$ NO

Inserire le parentesi mancanti

- $xyz(yx) → ((((x)y)z)(yx))$
- $λxyz.x(yz) → (λx. λy. λz.x(yz))$
- $ux(yz)(λv.vy) → ((((u)x)y)z)(λv.vy))$
- $λxyz.xz(yz) → (λx. λy. λz.(((x)z)y)z)$

Trova le FV:

- $FV(xv(λyz.yv)w)=\{x,v,v,w\}$

Fai la β-riduzione:

$$
(λx.λy.x)((λz.yz)(λw.w)) \\
→_β (λx.λy.x)(y(λw.w)) \\
\text{Rinominiamo }y \text{ a sinistra, perché è una FV a destra} \\
=_α (λx.λu.x)(y(λw.w)) \\
→_β (λu.y(λw.w))
$$
