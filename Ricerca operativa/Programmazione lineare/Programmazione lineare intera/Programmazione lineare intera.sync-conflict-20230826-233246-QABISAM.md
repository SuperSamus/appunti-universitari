# Programmazione lineare intera

($P_I$)
- $\max c·x$
- $A_x≤b$
- $x∈ℤ^n$

($D_I$)
- $\min y·b$
- $yA=c$
- $y∈ℤ^m_+$

Poliedri:
$P=\{x∈ℝ^n:Ax≤b\}\quad ჲ=\{y∈ℝ^m:yA=c\}$

Regioni ammissibili:
$S=P∩ℤ^n\quad T=ჲ∩ℤ^m$

## Rilassamenti continui

Prendere il problema intero e cancellare il vincolo di interezza.

(P)
- $\max c·x$
- $A_x≤b$

(D)
- $\min y·b$
- $yA=c$
- $y≥0$

Se $\bar{x}∈P$ soluzione ottima di (P) è a componenti intere, cioè $\bar{x}∈ℤ^n$, allora $\bar{x}$ è soluzione ottima di ($P_I$) (analogamente per ($D_I$))

Se tutti i vertici di P sono a componenti intere (**proprietà dell'interezza**), allora (P) ammette una soluzione ottima a componenti intere.

Se così non fosse, la [[Dualità#^b4e2a8|dualità debole]] continua a valere, ma non la [[Dualità#^2361d6|dualità forte]] non è più garantita. Nel caso generico, basarsi sul risultato del PL per ottenere quello del PLI è inutile, non hanno collegamenti.

### Involucro convesso del reticolo

$conv\:S=\{∑\limits_{i=1}^{n+1}λ_ix^i:x^i∈S,∑\limits_{i=1}^{n+1}λ_i=1,λ_i≥0\}$

Se $S$ è finito, allora $conv\:S$ è un poliedro con la proprietà dell'interezza e quindi:
$$
PLI \quad \begin{matrix}\max cx \\ x∈S\end{matrix} ≡ \begin{matrix}\max cx \\ x∈conv\:S\end{matrix} \quad PL
$$

Si cerca di avere il problema PL nella forma $conv\:S=\{x∈ℝ^n:\hat{A}x≤\hat{b}\}$, ma trovare $\hat{A}$ e $\hat{b}$ è difficile. Cercheremo di approssimarli meglio che si può.

Non sempre si può ottenere un poliedro.
Se $P=\{x∈ℝ^n:Ax≤b\}$ con $A∈ℤ^{m×n},b∈ℤ^m$, allora $conv(P∩ℤ^n)$ è un poliedro convesso.

Altrimenti, potrebbe non esserlo: per esempio: $P=\{x∈ℝ^2_+:x_2≥\sqrt{2}x_1\} \quad S=P∩ℤ^2$
$conv\:S=\{x∈ℝ^2_+:x_2>\sqrt{2}x_1\}$ non è un poliedro convesso.

#### Piano di taglio

Disuguaglianza valida: un vincolo di disuguaglianza soddisfatto da tutti i punti del reticolo intero. Per essere utile, deve tagliare una porzione del poliedro del PL, e preferibilmente taglia via la sua soluzione ottima (dato che non è ammissibile nel PLI).

##### Piani di taglio di Gomory

Eseguibile solo in (D).

Sia $\bar{y}=(\bar{y}_B,\bar{y_N})=(cA_B^{-1},0)$, soluzione ottima di base per (D).

Supponiamo $\bar{y}_r∉ℤ$ per qualche $r∈B$. Ci serve quindi un piano di taglio che butta fuori $\bar{y}$.

$\tilde{A}=A_NA_B^{-1}∈ℝ^{(m-n)×n}$ (è opportuno numerare le righe con gli indici di $N$, le colonne con gli indici di $B$)

Teorema:
- $∑\limits_{j∈N}\{\tilde{A}_{jr}\}\bar{y}_j≥\{\bar{y}_r\}$ è un piano di taglio
	- $\{x\}$ è la parte frazionaria di $x$
		- t3.2\}=0.8$e
	- È facile dimostrare che $\bar{y}$ non soddisfa questa disuguaglianza, e che quindi viene buttato fuori:
		- [[Dualità#^4e2ee6|Sappiamo]] che $\bar{y}_j=0 \quad j∈N$ 
		- Quindi $∑\limits_{j∈N}\{\tilde{A}_{jr}\}\bar{y}_j=0<\{\bar{y}_r\}$

Da dove salta fuori $\tilde{A}$?

$$
y∈ჲ∩ℤ^m→yA=c \\
\begin{bmatrix}y_B & y_N\end{bmatrix}\begin{bmatrix}A_B \\ A_N\end{bmatrix}=c↔y_BA_B+y_NA_N=c \\
y_BA_B=c-y_NA_N \\
y_B=cA_B^{-1}-y_NA_NA_B^{-1} \\
y_B=cA_B^{-1}-y_NA_NA_B^{-1} \\
y_B=\bar{y}_B-y_NA_NA_B^{-1} \\
y_B=\bar{y}_B-y_N\tilde{A}
$$

La dimostrazione su perché il reticolo intero sia tutto incluso nel piano di taglio non si trova qui.

###### Algoritmo

1. Si prende il problema in formato duale
	- Se il problema è in formato primale, si usano le [[Programmazione lineare#^4d0160|trasformazioni equivalenti]] per trasformarlo in formato duale (NON prendere il suo duale: la [[Dualità#^2361d6|dualità forte]] non è garantita). La soluzione non cambierà (anche se si potrebbero aggiungere scarti).
1. Se ne prende il rilassamento continuo
2. Si calcola una sua soluzione ottima di base
3. Se la soluzione è a componenti intere, STOP
4. Si calcola il piano di taglio, e si aggiunge la disuguaglianza ai vincoli del problema
5. Torna al punto 3.

Il metodo è detto *poliedrale*.