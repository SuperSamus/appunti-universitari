# Problema dello zaino

Abbiamo n oggetti da infilare in uno zaino.

- $p_i>0$ "peso" dell'oggetto $i$[^1]
- $b_i$ "beneficio" dell'oggetto $i$ se inserito nello zaino[^1]
- $c$ capacità dello zaino[^1]

Dobbiamo selettivamente inserire oggetti nello zaino per massimizzare il beneficio.

Per ogni oggetto, decidiamo se inserirlo o meno.

- $x_i \in \{0,1\}$, sarà 1 se infiliamo l'oggetto $i$ nello zaino, 0 altrimenti[^2]

Vincoli:

- $\displaystyle\sum_{i=1}^n p_ix_i \leq c$

Funzione obiettivo max: $f(x)=\displaystyle\sum_{i=1}^n b_ix_i$
[^1]: **Variabili quantitative**: rappresentano un valore numerico
[^2]: **Variabili logiche**: discriminano tra 2 scelte alternative