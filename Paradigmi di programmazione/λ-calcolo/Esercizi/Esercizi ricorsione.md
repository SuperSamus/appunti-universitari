# Esercizi [[ricorsione]]

Definire $fact$ sia con $Y$ che $\Theta$:

## Mult (con $add$)

$mult \: n \: m =_\beta mult' \: n \: m$

$mult' = \lambda f. \lambda n.\lambda m. ife(m==0,0,add \: n(f \: n (pred \: m)))$

$$
\Theta \: mult' \\
\rightarrow_\beta mult'(\Theta \: mult') \\
\rightarrow_\beta \lambda n.\lambda m. ife(m==0,0,add \: n((\Theta \: mult')n(pred \: m)))
$$

## Fact
