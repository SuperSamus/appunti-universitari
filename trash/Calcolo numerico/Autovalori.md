Una matrice trasforma vettori in altri vettori. È possibile che dei vettori vengono trasformati in modo tale da essere semplicemente scalati. Questi sono gli **autovettori**.
Di quanto sono scalati si misura con gli **autovalori**.

Abbiamo quindi autovettori $v$ scalati di $λ$:
$Av=λv$

Dato $n$ la dimensione della matrice quadrata, in $ℝ$, è possibile che ogni vettore sia un'autovettore (matrici diagonali), che ci siano $n$ autovettori (il caso tipico), o che ci siano meno di $n$ autovettori (rotazioni, stiramenti...).

$ρ(A)$ indica il modulo massimo degli autovalori.

### Come trovare gli autovalori?

$Av-λv=0$
$Av-λIv=0$
$(A-λI)v=0$
$\det(A-λI)=0$

Trova quindi i λ tali che $\det(A-λI)=0$.
Poi, per ciascun autovalore λ trova $v$ tale che $(A-λI)v=0$.

### A cosa serve?

Normalmente, applicare la stessa trasformazione $n$ volte è difficile, ma se l'input è un autovettore è facile: viene semplicemente scalato di $λ^n$.

Difficilmente però l'input è già un autovettore, ma lo si può rendere tale.
Se una matrice quadrata ha $n$ autovettori, questi vettori possono essere usati come matrice $B$ per fare un cambio di base:
$C=B^{-1}AB$
Questa matrice sarà sempre diagonale.
Quindi, per applicare A $n$ volte a un vettore $v$:
$w=BC^nB^{-1}$

### Cerchi di Gershgorin

Ogni autovalore (per ogni riga $i$) è localizzabile in un cerchio (in ℂ) del seguente raggio:
$R_i(A)=∑\limits_{j=1,i≠j}^n|a_{ij}|$
Localizzati in posizione $a_{ii}$, quindi l'autovalore della riga $i$ si trova in:
$K_i:=\{z∈ℂ:|z-a_{ii}≤R_i(A)\}$

"Riga" e "colonna" sono scambiabili nelle definizioni sopra. Calcolando i raggi sia per riga che per colonna, i cerchi finali sono l'intersezione dei risultati.