## Esempio 1

Trovare un piano di Gomory per:

Funzione obiettivo: $\max x_2$

Vincoli:
- $3x_1+2x_2≤6$
- $-3x_1+2x_2≤0$
- $x_1,x_2∈ℤ_+$

Col problema rilassato, la soluzione di base primale è $\bar{x}=(1,\frac{3}{2})$, con $B=\{1,2\}$.

Dobbiamo [[Programmazione lineare#^4d0160|trasformare]] il problema in formato duale.

Funzione obiettivo: $\min -x_2$

Vincoli:
- $3x_1+2x_2+s_1=6$
- $-3x_1+2x_2+s_2=0$
- $x_1,x_2≥0$
- $s_1,s_2≥0$

(Quindi, $y=(x_1,x_2,s_1,s_2)$)

- $b=\begin{bmatrix}0 \\ -1 \\ 0 \\ 0\end{bmatrix}$
- $c=\begin{bmatrix}6 & 0\end{bmatrix}$
- $A=\begin{bmatrix}3 & -3 \\ 2 & 3 \\ 1 & 0 \\ 0 & 1\end{bmatrix}$

Soluzione ottima: $\bar{y}=(1,\frac{3}{2},0,0)$ (il fatto che gli scarti siano $0$ è un caso)
- $r=2$
- $B=\{1,2\}$
- $N=\{3,4\}$

$\tilde{A}=A_NA_B^{-1}=\begin{bmatrix}1 & 0 \\ 0 & 1\end{bmatrix}\begin{bmatrix}\frac{1}{6} & \frac{1}{4} \\ -\frac{1}{6} & \frac{1}{4}\end{bmatrix}=\begin{bmatrix}\frac{1}{6} & \frac{1}{4} \\ -\frac{1}{6} & \frac{1}{4}\end{bmatrix}$

(Ricorda che si numerano le righe con gli indici di $N$, le colonne con gli indici di $B$)

Aggiungiamo quindi il vincolo: $∑\limits_{j∈N}\{\tilde{A}_{jr}\}\bar{y}_j≥\{\bar{y}_r\}→\{\frac{1}{4}\}y_3+\{\frac{1}{4}\}y_4≥\{\frac{3}{2}\}→\frac{1}{4}s_1+\frac{1}{4}s_2≥\frac{1}{2}→s_1+s_2≥2$

Per portare il vincolo alla forma originale:
- $s_1=6-3x_1-2x_2$
- $s_2=3x_1-2x_2$

$s_1+s_2≥2→6-3x_1-2x_2+3x_1-2x_2≥2→-4x_2≥-4→x_2≤1$

## Esempio 2

Funzione obiettivo: $\max x_1$

Vincoli:
- $2x_1+7x_2≤7$
- $x_2≤2$
- $x_1,x_2∈ℤ_+$

Col problema rilassato, la soluzione di base primale è $\bar{x}=(\frac{7}{2},0)$, con $B=\{1\}$.

Dobbiamo [[Programmazione lineare#^4d0160|trasformare]] il problema in formato duale.

Funzione obiettivo: $\min -x_1$

Vincoli:
- $2x_1+7x_2+s_1=7$
- $x_2+s_2=2$
- $x_1,x_2∈ℤ_+$
- $s_1,s_2≥0$

(Quindi, $y=(x_1,x_2,s_1,s_2)$)

- $b=\begin{bmatrix}-1 \\ 0 \\ 0 \\ 0\end{bmatrix}$
- $c=\begin{bmatrix}7 & 2\end{bmatrix}$
- $A=\begin{bmatrix}2 & 0 \\ 7 & 1 \\ 1 & 0 \\ 0 & 1\end{bmatrix}$

Soluzione ottima: $\bar{y}=(\frac{7}{2},0,0,2)$
- $r=1$
- $B=\{1,4\}$
- $N=\{2,3\}$

$\tilde{A}=A_NA_B^{-1}=\begin{bmatrix}7 & 1 \\ 1 & 0\end{bmatrix}\begin{bmatrix}\frac{1}{2} & 0 \\ 0 & 1\end{bmatrix}=\begin{bmatrix}\frac{7}{2} & 1 \\ \frac{1}{2} & 0\end{bmatrix}$

(Ricorda che si numerano le righe con gli indici di $N$, le colonne con gli indici di $B$)

Aggiungiamo quindi il vincolo: $∑\limits_{j∈N}\{\tilde{A}_{jr}\}\bar{y}_j≥\{\bar{y}_r\}→\{\frac{7}{2}\}y_2+\{\frac{1}{2}\}y_3≥\{\frac{7}{2}\}→\frac{1}{2}x_2+\frac{1}{2}s_1≥\frac{1}{2}→x_2+s_1≥1$

Per portare il vincolo alla forma originale:
- $s_1=7-2x_1-7x_2$

$x_2+s_1≥1→x_2+7-2x_1-7x_2≥1→-2x_1-6x_2≥-6→x_1+3x_2≤3$

## Esempio 3

Funzione obiettivo: $\max x_1+x_2$

Vincoli:
- $12x_1+2x_2≤36$
- $-2x_1+2x_2≤3$
- $x_2≤2$
- $x_1,x_2∈ℤ_+$

Col problema rilassato, la soluzione di base primale è $\bar{x}=(\frac{8}{3},2)$, con $B=\{1,3\}$.

Dobbiamo [[Programmazione lineare#^4d0160|trasformare]] il problema in formato duale.

Funzione obiettivo: $\min -x_1-x_2$

Vincoli:
- $12x_1+2x_2+s_1=36$
- $-2x_1+2x_2+s_2=3$
- $x_2+s_3=2$
- $x_1,x_2∈ℤ_+$
- $s_1,s_2,s_3≥0$

(Quindi, $y=(x_1,x_2,s_1,s_2,s_3)$)

- $b=\begin{bmatrix}-1 \\ -1 \\ 0 \\ 0 \\ 0\end{bmatrix}$
- $c=\begin{bmatrix}36 & 3 & 2\end{bmatrix}$
- $A=\begin{bmatrix}12 & -2 & 0 \\ 2 & 2 & 1 \\ 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1\end{bmatrix}$

Soluzione ottima: $\bar{y}=(\frac{8}{3},2,0,13,0)$
- $r=1$
- $B=\{1,2,4\}$
- $N=\{3,5\}$

$\tilde{A}=A_NA_B^{-1}=\begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 1\end{bmatrix}\begin{bmatrix}\frac{1}{12} & 0 & \frac{1}{6} \\ 0 & 0 & 1 \\ -\frac{1}{6} & 1 & -\frac{7}{3}\end{bmatrix}=\begin{bmatrix}\frac{1}{12} & 0 & \frac{1}{6} \\ -\frac{1}{6} & 1 & -\frac{7}{3}\end{bmatrix}$

(Ricorda che si numerano le righe con gli indici di $N$, le colonne con gli indici di $B$)

Aggiungiamo quindi il vincolo: $∑\limits_{j∈N}\{\tilde{A}_{jr}\}\bar{y}_j≥\{\bar{y}_r\}→\{\frac{1}{12}\}y_3+\{-\frac{1}{6}\}y_5≥\{\frac{8}{3}\}→\frac{1}{12}s_1+\frac{5}{6}s_3≥\frac{2}{3}→s_1+10s_3≥8$

Per portare il vincolo alla forma originale:
- $s_1=36-12x_1-2x_2$
- $s_3=2-x_2$

$s_1+10s_3≥8→36-12x_1-2x_2+20-10x_2≥8→-12x_1-12x_2≥-48→x_1+x_2≤4$
