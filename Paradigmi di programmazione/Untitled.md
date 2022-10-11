$$
(λx.λy.x)((λz.yz)(λw.w)) \\
→_β (λx.λy.x)(y(λw.w)) \\
\text{Rinominiamo }y \text{ a sinistra, perché è una FV a destra} \\
=_α (λx.λu.x)(y(λw.w)) \\
→_β (λu.y(λw.w))
$$

$k≜λx.λy.x$
$Θ≜AA$
$A≜λx.λy.y(xxy)$
$Θk=k(Θk)=(λx.λy.x)(Θk)→_β λy.Θk=O$ Ogre
$Ot→_β O$

Combinatori

TODO

$k,s≜λx.λy.λz.xz(yz)$
$kxy→_w x$
$sxyz →_w xz(yz)$
$t::=x|s|k|tt$

```mermaid
flowchart LR
F --> Λ --> C
```
