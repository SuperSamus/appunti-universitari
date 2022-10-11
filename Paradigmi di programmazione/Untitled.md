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
