# Esempio [[Dualità#^a27b21|simplesso duale]]

(D)

Funzione obiettivo: $\min 3y_2-2y_3-3y_4+4y_6$

Vincoli:
- $-y_2+y_3+2y_4+y_5=0$
- $y_1+y_3+y_4-y_6=-1$
- $y_1,y_2,y_3,y_4,y_5,6_6≥0$

- $b=\begin{bmatrix}0 \\ 3 \\ -2 \\ -3 \\ 0 \\ 4\end{bmatrix}$
- $A=\begin{bmatrix}0 & 1 \\ -1 & 0 \\ 1 & 1 \\ 2 & 1 \\ 1 & 0 \\ 0 & -1\end{bmatrix}$
- $c=(0,-1)$

Prendiamo la base $B=\{3,6\}$

(P)

Funzione obiettivo: $\max -x_2$

Vincoli:
- $x_2≤0$
- $-x_1≤3$
- $x_1+x_2≤-2$
- $2x_1+x_2≤-3$
- $x_1≤0$
- $-x_2≤4$

- $A_B=\begin{bmatrix}1 & 1 \\ 0 & -1\end{bmatrix}$
- $A_B^{-1}=\begin{bmatrix}1 & 1 \\ 0 & -1\end{bmatrix}$
- $\bar{y}_B=cA_B^{-1}=(0,-1)\begin{bmatrix}1 & 1 \\ 0 & -1\end{bmatrix}=\begin{bmatrix}0 \\ 1\end{bmatrix}$
	- $\bar{y}=(0,0,0,0,0,1)$ è ammissibile
- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}1 & 1 \\ 0 & -1\end{bmatrix}\begin{bmatrix}-2 \\ 4\end{bmatrix}=\begin{bmatrix}2 \\ -4\end{bmatrix}$
	- Il vincolo 4, cioè $2*2-4=2>-3$, e il vincolo 5, cioè $x_1=2>0$, non sono verificati
- $k=\min\{4,5\}=4$
- $η_B=A_kA_B^{-1}=\begin{bmatrix}2 & 1\end{bmatrix}\begin{bmatrix}1 & 1 \\ 0 & -1\end{bmatrix}=\begin{bmatrix}2 \\ 1\end{bmatrix}$
	- $η_3=2$
	- $η_6=1$
- Direzione di decrescita $d=(0,0,-2,1,0,-1)$
	- $θ_3=\frac{\bar{y}_3}{η_3}=0$
	- $θ_6=\frac{\bar{y}_6}{η_6}=1$
	- $\bar{θ}=\min\{θ_3.θ_6\}=0$
	- $h=3$

Nuova base $B'=B∪\{h\}∖\{k\}=\{4,6\}$, con lo stesso $y$ (dato che $θ=0$, quindi $y+θd=0$)