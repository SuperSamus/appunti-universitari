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

## Problema 3

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

## Problema 4

^84747c

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
	- $\bar{y}=(0,0,0,1,-3)$ non ammissibile

Esisterà una direzione di [[Dualità#^247330|crescita]].

Cerchiamo di eliminare l'elemento problematico della base:

- $h∈B \text{ t.c. } \bar{y}_h<0$ indice uscente
	- Qui, $h=5$.
- $B(h)=$ posizione di $h$ nella base
	- Qui, $B(h)=2$
- $u_{B(h)}∈ℝ^n \text{ t.c. } [u_{B(h)}]_i=\begin{cases}1 & i=B(h) \\ 0 & i≠B(h)\end{cases}$
- $ξ=-A_B^{-1}u_{B(h)}=\begin{bmatrix}0 & 1 \\ -1 & 1\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 1\end{bmatrix}$
	- È sostanzialmente la $B(h)$-esima colonna di $-A_B^{-1}$
	- $c·ξ=-cA_B^{-1}u_{B(h)}=-\bar{y}_B·u_{B(h)}=-\bar{y}_h>0$
	- $A_Bξ=-A_BA_B^{-1}u_{B(h)}=-u_B(h)≤0$
		- $A_iξ=\begin{cases}-1 & \text{se }i=h \\ 0 & \text{se }i≠h\end{cases}$
			- Questo vuol dire che se ci si sposta da $\bar{x}$ di un passo $λ$ nella direzione $ξ$:
			- $\bar{x}+λξ\quad A_i(\bar{x}+λξ)=A_i\bar{x}+λA_iξ=\begin{cases}A_i\bar{x}=b & i≠h \\ <A_i\bar{x}=b & i=h\end{cases}$
			- Detto in altro modo: tutti vincoli della base rimangono attivi.
	- Spostandoci anche all'infinito continueremo a rispettare i vincoli appartenenti alla base. Ma di quanto ci si può spostare al massimo $\bar{λ}_i$ rispettando i vincoli non appartenenti alla base? Sfruttiamo quello che [[Dualità#^ff2cae|abbiamo visto]]: troviamo le condizioni che soddisfano $i∈N\quad A_i(\bar{x}+λξ)=A_i\bar{x}+λA_iξ\stackrel{?}{≤}b_i$
		- $\bar{λ}_i=+∞$ se $A_iξ≤0$
			- $A_i(\bar{x}+λξ)≤A_i\bar{x}≤b_i$
		- $\bar{λ}_i=\cfrac{b_i-A_i\bar{x}}{A_iξ}$ se $A_iξ>0$:
			- $A_i\bar{x}+λA_iξ≤b_i⇔λ≤\cfrac{b_i-A_i\bar{x}}{A_iξ}$ (che è $>0$)
		- $\bar{λ}=\min\{\bar{λ}_i:i∈N\}$ è il massimo spostamento "ammissibile"

