# Esempio [[dualità]]

Problema in formato (P):

Funzione obiettivo: $\max x_1+2x_2$

Vincoli:
- $x_2≤4$
- $x_1+2x_2≤2$
- $x_1≤0$
- $x_1-x_2≤-2$
- $x_1+2x_2≤-2$

$\bar{x}=(-2,4)$ è ottima?

- $c=(1\;2)$
- $A=\begin{bmatrix}0 & 1 \\ 1 & 1 \\ 1 & 0 \\ 1 & -1 \\ 1 & -2\end{bmatrix}$
- $b=\begin{bmatrix}4 \\ 2 \\0 \\ -2 \\ -2 \end{bmatrix}$

Problema duale (D):

Funzione obiettivo: $\min 4y_1+2y_2-2y_4-2y_5$

Vincoli:
- $y_2+y_3+y_4+y_5=1$
- $y_1+y_2-y_4-2y_5=2$
- $y_1.y_2,y_3,y_4,y_5≥0$
