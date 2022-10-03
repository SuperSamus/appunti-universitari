# Esercizi [[ricorsione]]

## Mult

Definire $mult'$ tramite $fix$ (e $add$).

$mult \: n \: m =_\beta mult' \: n \: m$

$mult' = \lambda f. \lambda n.\lambda m. ife(m==0,0,add \: n(f \: n (pred \: m)))$

$$
fix \: mult' \\
\rightarrow_\beta mult'(fix \: mult') \\
\rightarrow_\beta \lambda n.\lambda m. ife(m==0,0,add \: n((fix \: mult')n(pred \: m)))
$$

## Fact

Definire $fact$ sia con $Y$ che $\Theta$.