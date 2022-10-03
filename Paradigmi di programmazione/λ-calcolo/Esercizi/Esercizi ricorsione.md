# Esercizi [[ricorsione]]

Definire $fact$ sia con $Y$ che $\Theta$:

## Mult (con $add$)

$mult \: n \: m =_\beta mult' \: n \: m$

$mult' = \lambda f. \lambda n.\lambda m. ife(m==0,0,add \: n(f \: n (pred \: m)))$

$\Theta \: mult' = \lambda f. \lambda n.\lambda m. ife(m==0,0,add \: n(f \: n (pred \: m)))$

## Fact

## Exp (anche direttamente)

## Pred