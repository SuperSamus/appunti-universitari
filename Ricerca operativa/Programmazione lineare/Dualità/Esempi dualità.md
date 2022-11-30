# Esempi [[dualità]]

## Problema 1

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

## Problema 2

(P)

Funzione obiettivo: $\max x_1+2x_2$

Vincoli:
- $x_2≤4$
- $x_1+x_2≤2$
- $x_1≤0$
- $x_1-x_2≤-2$
- $x_1-2x_2≤-2$

- $c=(1,2)$
- $A=\begin{bmatrix}0 & 1 \\ 1 & 1 \\ 1 & 0 \\ 1 & -1 \\ 1 & -2\end{bmatrix}$
- $b=\begin{bmatrix}4 \\ 2 \\ 0 \\ -2 \\ -2 \end{bmatrix}$

$\bar{x}=(-2,4)$ è ottima?

(D)

Funzione obiettivo: $\min 4y_1+2y_2-2y_4-2y_5$

Vincoli:
- $y_2+y_3+y_4+y_5=1$
- $y_1+y_2-y_4-2y_5=2$
- $y_1.y_2,y_3,y_4,y_5≥0$

Usiamo il [[Dualità#^4e2ee6|teorema degli scarti complementari]].

- $I(\bar{x})=\{1,2\}$
- $\bar{y}_3=\bar{y}_4=\bar{y}_5=0$
- $y_1,y_2≥0$
	- $\bar{y}_1=\bar{y}_2=1$
	- $\bar{y}=(1,1,0,0,0)$

Urrà! $\bar{x}$ è ottima.

---

Cosa succede se cambiano la funzione obiettivo in $c=\{α,β\}$? Per quali valori di $α$ e $β$, $\bar{x}$ rimane ottima?

- $y_2+y_3+y_4+y_5=α$
- $y_1+y_2-y_4-2y_5=β$
- $y_1.y_2,y_3,y_4,y_5≥0$

Quindi:
- $\bar{y}_2=α$
- $\bar{y}_1+\bar{y}_2=β→\bar{y}_1=β-α$

Allora $\bar{y}=\{β-α,α,0,0,0\}$, con $β≥α≥0$.

### Cambiamo dati

(P)

Funzione obiettivo: $\max x_2$

Vincoli:
- $x_2≤4$
- $x_1+x_2≤2$
- $x_1≤0$
- $x_1-x_2≤-2$
- $x_1-2x_2≤-2$

- $c=(0,1)$
- $A=\begin{bmatrix}0 & 1 \\ 1 & 1 \\ 1 & 0 \\ 1 & -1 \\ 1 & -2\end{bmatrix}$
- $b=\begin{bmatrix}4 \\ 2 \\0 \\ -2 \\ -2 \end{bmatrix}$

$\bar{x}=(0,2)$ è ottima?

(D)

Funzione obiettivo: $\min 4y_1+2y_2-2y_4-2y_5$

Vincoli:
- $y_2+y_3+y_4+y_5=0$
- $y_1+y_2-y_4-2y_5=1$
- $y_1.y_2,y_3,y_4,y_5≥0$

- $I(\bar{x})=\{2,3,4\}$
- $\bar{y}_1=\bar{y}_5=0$
- $y_2,y_3,y_4≥0$
	- $y_2+y_3+y_4=0$
	- $y_2-y_4=1$
	- Questo è impossibile: la prima condizione chiede che siano tutti uguali a 0, ma ciò impedisce di soddisfare la seconda condizione.

$\bar{x}$ non è ottimo. Cerchiamo di farlo [[Dualità#^247330|crescere]].

$ξ$ direzione ammissibile per $\bar{x}⇔A_{I(\bar{x})}≤0$

$A_{I(\bar{x})}ξ=\begin{bmatrix} 1 & 1 \\ 1 & 0 \\ 1 & -1\end{bmatrix}\begin{bmatrix}ξ_1 \\ ξ_2\end{bmatrix}≤0⇔\begin{cases}ξ_1+ξ_2≤0 \\ ξ_1≤0 \\ ξ_1-ξ_2≤0\end{cases}$

Il sistema descrive il [[Programmazione lineare#^15fa21|cono]] dove può crescere.

# Problema 3

(P)

Funzione obiettivo: $\max -x_1+2x_2$

Vincoli:
- $x_1-x_2≤1$
- $x_2≤2$
- $x_1+x_2≤3$
- $-x_1+x_2≤1$
- $-x_1≤0$

- $c=(-1,2)$
- $A=\begin{bmatrix}1 & -1 \\ 0 & 1 \\ 1 & 1 \\ -1 & 1 \\ -1 & 0\end{bmatrix}$
- $b=\begin{bmatrix}1 \\ 2 \\ 3 \\ 1 \\ 0 \end{bmatrix}$

$\bar{x}=(1,2)$ è ottima?

$I(\bar{x})=\{2,3,4\}$

Argh, è [[Dualità#^e880fd|degenere]]. Proviamo la base $B=\{2,3\}$.
- $N=\{1,4,5\}$
- $A_B=\begin{bmatrix}0 & 1 \\ 1 & 1\end{bmatrix}$
- $A_B^{-1}=\begin{bmatrix}-1 & 1 \\ 1 & 0\end{bmatrix}$

- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}-1 & 1 \\ 1 & 0\end{bmatrix}\begin{bmatrix}2 \\ 3\end{bmatrix}=\begin{bmatrix}1 \\ 2\end{bmatrix}$
- $\bar{y}=cA_B^{-1}=\begin{bmatrix}-1 & 2\end{bmatrix}\begin{bmatrix}-1 & 1 \\ 1 & 0\end{bmatrix}=\begin{bmatrix}3 & -1\end{bmatrix}$
	- $\bar{y}=(0,3,-1,0,0)$
	- $\bar{y}_3<0$, quindi non è ammissibile
		- Non vuol dire che $\bar{x}$ non sia ottima. Dobbiamo provare le altre basi.

Proviamo la base $B=\{2,4\}$.
- $N=\{1,3,5\}$
- $A_B=\begin{bmatrix}0 & 1 \\ -1 & 1\end{bmatrix}$
- $A_B^{-1}=\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}$

- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}\begin{bmatrix}2 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 2\end{bmatrix}$
- $\bar{y}=cA_B^{-1}=\begin{bmatrix}-1 & 2\end{bmatrix}\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}=\begin{bmatrix}1 & 1\end{bmatrix}$
	- $\bar{y}=(0,1,0,1,0)$
	- Questa è ammissibile. $\bar{x}$ è ottima.

# Problema 4

(P)

Funzione obiettivo: $\max 2x_1+x_2$

Vincoli:
- $x_1-x_2≤1$
- $x_2≤2$
- $x_1+x_2≤3$
- $-x_1+x_2≤1$
- $-x_1≤0$

- $c=(2,1)$
- $A=\begin{bmatrix}1 & -1 \\ 0 & 1 \\ 1 & 1 \\ -1 & 1 \\ -1 & 0\end{bmatrix}$
- $b=\begin{bmatrix}1 \\ 2 \\ 3 \\ 1 \\ 0 \end{bmatrix}$

Stavolta prendiamo il vertice da una base. Scegliamo $B=\{4,5\}$:
- $N=\{1,2,3\}$
- $A_B=\begin{bmatrix}-1 & 1 \\ -1 & 0\end{bmatrix}$
- $A_B^{-1}=\begin{bmatrix}0 & -1 \\ 1 & -1\end{bmatrix}$
- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}0 & -1 \\ 1 & -1\end{bmatrix}\begin{bmatrix}1 \\ 0\end{bmatrix}=\begin{bmatrix}0 \\ 1\end{bmatrix}$
- $I(\bar{x})=\{4,5\}=B$, non degenere
- $\bar{y}=cA_B^{-1}=\begin{bmatrix}2 & 1\end{bmatrix}\begin{bmatrix}0 & -1 \\ 1 & -1\end{bmatrix}=\begin{bmatrix}1 & -3\end{bmatrix}$
