# Esempi[[dualità]]

## 1

(P)

Funzione obiettivo: $\max 3x_1+2x_2$

Vincoli:
- $x_1-x_2≤1$
- $x_1+x_2≤3$
- $-x_1+x_2≤1$

$\bar{x}=(2,1)$ è soluzione ottima?

- $c=(3,2)$
- $A=\begin{bmatrix}1 & -1 \\ 1 & 1 \\ -1 & 1 \end{bmatrix}$
- $b=\begin{bmatrix}1 \\ 3 \\ 1\end{bmatrix}$

$c·\bar{x}=8$

(D)

Funzione obiettivo: $\min y_1+3y_2+y_3$

Vincoli:
- $\begin{bmatrix} y_1 & y_2 & y_3 \end{bmatrix}A=\begin{bmatrix} c_1 \\ c_2 \end{bmatrix}$
	- $y_1+y_2-y_3=3$
	- $-y_1+y_2+y_3=2$
- $\bar{y}·b=c·\bar{x}$
	- $y_1+3y_2+y_3=8$
- $y_1,y_2,y_3≥0$

Si risolve $y_1=\frac{1}{2},y_2=\frac{5}{2},y_3=0$, che è una soluzione ammissibile.

Quindi $\bar{x}=(2,1)$ è soluzione ottima.

---

Con il [[Dualità#^15b491|lemma di Farkas]]:

$I(\bar{x})=\{1,2\}$
- $y_{I(\bar{x})}=\begin{bmatrix} y_1 & y_2 \end{bmatrix}$
- $A_{I(\bar{x})}=\begin{bmatrix} A_1 \\ A_2 \end{bmatrix}$

$y_{I(\bar{x})}A_{I(\bar{x})}=c→\begin{bmatrix} y_1 & y_2 \end{bmatrix}\begin{bmatrix} 1 & -1 \\ 1 & 1 \end{bmatrix}=\begin{bmatrix} 3 \\ 2 \end{bmatrix}$

Riotteniamo gli stessi risultati: $\begin{cases}y_1+y_2=3 \\ -y_1+y_2=2 \end{cases}→y_2=\frac{5}{2}→y_1=\frac{1}{2}$

## 2

(P)

Funzione obiettivo: $\max x_1+2x_2$

Vincoli:
- $x_2≤4$
- $x_1+x_2≤2$
- $x_1≤0$
- $x_1-x_2≤-2$
- $x_1-2x_2≤-2$

- $c=(1\;2)$
- $A=\begin{bmatrix}0 & 1 \\ 1 & 1 \\ 1 & 0 \\ 1 & -1 \\ 1 & -2\end{bmatrix}$
- $b=\begin{bmatrix}4 \\ 2 \\0 \\ -2 \\ -2 \end{bmatrix}$

$\bar{x}=(-2,4)$ è ottima?

(D)

Funzione obiettivo: $\min 4y_1+2y_2-2y_4-2y_5$

Vincoli:
- $y_2+y_3+y_4+y_5=1$
- $y_1+y_2-y_4-2y_5=2$
- $y_1.y_2,y_3,y_4,y_5≥0$

Usiamo il [[Dualità#^4e2ee6|teorema degli scarti complementari]].

- $I(\bar{x})=\{1,2\}$
- $\bar{y_3}=\bar{y_4}=\bar{y_5}=0$
- $y_1,y_2≥0$
	- $\bar{y_1}=\bar{y_2}=1$
	- $\bar{y}=(1,1,0,0,0)$
