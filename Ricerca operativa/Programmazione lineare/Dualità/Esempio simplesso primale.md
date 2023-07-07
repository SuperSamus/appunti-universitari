# Esempio [[Dualità#^7f28a7|simplesso primale]]

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
- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}0 & -1 \\ 1 & -1\end{bmatrix}\begin{bmatrix}1 \\ 0\end{bmatrix}=\begin{bmatrix}0 \\ 1\end{bmatrix}$, è ammissibile
- $I(\bar{x})=\{4,5\}=B$, non degenere
- $\bar{y}=cA_B^{-1}=\begin{bmatrix}2 & 1\end{bmatrix}\begin{bmatrix}0 & -1 \\ 1 & -1\end{bmatrix}=\begin{bmatrix}1 & -3\end{bmatrix}$
	- $\bar{y}=(0,0,0,1,-3)$ non ammissibile

Esisterà una direzione di [[Dualità#^247330|crescita]].

Cerchiamo di rimuovere l'elemento problematico della base:

- $h∈B \text{ t.c. } \bar{y}_h<0$ **indice uscente**
	- Qui, $h=5$.
- $B(h)=$ indice di $h$ relativamente alla base
	- Qui, $B(h)=2$
- $u_{B(h)}∈ℝ^n \text{ t.c. } [u_{B(h)}]_i=\begin{cases}1 & i=B(h) \\ 0 & i≠B(h)\end{cases}$
- $ξ=-A_B^{-1}u_{B(h)}=\begin{bmatrix}0 & 1 \\ -1 & 1\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 1\end{bmatrix}$
- Spostandoci (anche all'infinito) continueremo a rispettare i vincoli appartenenti alla base. Ma di quanto ci si può spostare al massimo $\bar{λ}_i$ rispettando i vincoli non appartenenti alla base? Sfruttiamo quello che [[Dualità#^ff2cae|abbiamo visto]].
	- $\bar{λ}_1=+∞←\begin{bmatrix}1 & -1\end{bmatrix}\begin{bmatrix}1 \\ 1\end{bmatrix}=0≤0$
	- $\bar{λ}_2=\cfrac{2-\begin{bmatrix}0 & 1\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix}}{\begin{bmatrix}0 & 1\end{bmatrix}\begin{bmatrix}1 \\ 1\end{bmatrix}}=1$
	- $\bar{λ}_3=\cfrac{3-\begin{bmatrix}1 & 1\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix}}{\begin{bmatrix}1 & 1\end{bmatrix}\begin{bmatrix}1 \\ 1\end{bmatrix}}=1$
	- $\bar{λ}=\min\{+∞,1,1\}=1$

Finalmente: $\bar{x}+\bar{λ}\bar{ξ}=\begin{bmatrix}0 \\ 1\end{bmatrix}+1\begin{bmatrix}1 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 2\end{bmatrix}$

Agli indici attivi si aggiungono tutti quelli di spostamento minimo:
$k∈N \text{ t.c }\bar{λ}=\bar{λ}_k$ **indice entrante**

$B_{nuova}=B∖\{h\}∪\{k\}$ è una base di cui $\bar{x}+\bar{λ}\bar{ξ}$ è soluzione primale di base ammissibile (→vertice)


Abbiamo il nuovo $I(\bar{x})=\{2,3,4\}$

Rifacciamo tutti i conti con la nuova base $B=\{2,4\}$ (stavolta è [[Dualità#^e880fd|degenere]], abbiamo escluso $3$):
- $A_B=\begin{bmatrix}0 & 1 \\ -1 & 1\end{bmatrix}$
- $A_B^{-1}=\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}$
- $\bar{x}=A_B^{-1}b_B=\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}\begin{bmatrix}2 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 2\end{bmatrix}$
- $\bar{y}=cA_B^{-1}=\begin{bmatrix}2 & 1\end{bmatrix}\begin{bmatrix}1 & -1 \\ 1 & 0\end{bmatrix}=\begin{bmatrix}3 & -2\end{bmatrix}$
	- $\bar{y}=(0,3,0,-2,0)$ non ammissibile

Se proviamo a crescere, otterremo $ξ=-A_B^{-1}u_{B(h)}=\begin{bmatrix}-1 & 1 \\ -1 & 0\end{bmatrix}\begin{bmatrix}0 \\ 1\end{bmatrix}=\begin{bmatrix}1 \\ 0\end{bmatrix}$, che non è [[Dualità#^ff2cae|ammissibile]] perché $A_3ξ=\begin{bmatrix}1 & 1\end{bmatrix}\begin{bmatrix}1 \\ 0\end{bmatrix}=1>0$.

Però, si potrebbe dire che $\bar{λ}=0$, che ci ridà lo stesso $\bar{x}$. È ora di provare una nuova base (**cambiamento di base degenere**).