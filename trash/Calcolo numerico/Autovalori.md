Una matrice trasforma vettori in altri vettori. È possibile che dei vettori vengono trasformati in modo tale da essere semplicemente scalati. Questi sono gli **autovettori**.
Di quanto sono scalati si misura con gli **autovalori**.

Abbiamo quindi autovettori $v$ scalati di $λ$:
$Av=λv$

Dato $n$ la dimensione della matrice quadrata, in $ℝ$, è possibile che ogni vettore sia un'autovettore (matrici diagonali), che ci siano $n$ autovettori (il caso tipico), o che ci siano meno di $n$ autovettori (rotazioni, stiramenti…).

Se $A$ ha $n$ autovalori (avere autovalori uguali per autovettori diversi conta):
- Il suo *determinante* è uguale al prodotto degli autovalori.
- La sua *traccia* (somma di elementi in diagonale) è uguale alla somma degli autovalori

Gli autovalori di una matrice inversa sono il reciproco degli autovalori della matrice originale.

Se due matrici hanno autovalori, rango, determinante e traccia uguali, sono **simili**.

$ρ(A)$ indica il modulo massimo degli autovalori.

### Come trovare gli autovalori?

$Av-λv=0$
$Av-λIv=0$
$(A-λI)v=0$
$\det(A-λI)=0$

Trova quindi i $λ$ tali che $\det(A-λI)=0$.
Poi, per ciascun autovalore $λ$ trova $v$ tale che $(A-λI)v=0$.

### A cosa serve?

Normalmente, data una trasformazione $A$, applicarla $n$ volte è difficile, ma se l'input è un autovettore è facile: viene semplicemente scalato di $λ^n$.

Difficilmente però l'input è già un autovettore,.
Se una matrice quadrata ha $n$ autovettori, questi possono essere usati come matrice diagonale $P$ per fare un cambio di base:
$D=P^{-1}AP$
$D$ sarà sempre diagonale (quindi applicarla $n$ volte è facile), ed è *simile* ad A.

Quindi, per applicare A $n$ volte a un vettore $v$:
$w=PD^nP^{-1}v$

### Cerchi di Gershgorin

Ogni autovalore (per ogni riga $i$) è localizzabile in un cerchio (in ℂ) del seguente raggio:
$R_i(A)=∑\limits_{j=1,i≠j}^n|a_{ij}|$
Localizzati in posizione $a_{ii}$, quindi l'autovalore della riga $i$ si trova in:
$K_i:=\{z∈ℂ:|z-a_{ii}≤R_i(A)\}$

"Riga" e "colonna" sono scambiabili nelle definizioni sopra. Calcolando i raggi sia per riga che per colonna, i cerchi finali sono l'intersezione dei risultati.

Una matrice a predominanza diagonale non può avere autovalori 0, ad è quindi invertibile.

## Metodo delle potenze

Nella situazione in cui una matrice $A$ ha un autovalore $λ_1$ di modulo strettamente maggiore rispetto agli altri, intuitivamente, applicare la trasformazione su un qualunque vettore $v$ farà sì che il vettore tenderà sempre di più ad essere l'autovettore $x_1$ (cioè quello associato a $λ_1$).

Matematicamente, definendo $v$ come:
$v=∑\limits_{i=1}^nα_ix_i$

Si può applicare $A$ un numero $k$ di volte:
$A^kv=A^k∑\limits_{i=1}^nα_ix_i=∑\limits_{i=1}^nα_iA^kx_i=∑\limits_{i=1}^nα_iλ_i^kx_i=λ_1^k(α_1x_1+∑\limits_{i=2}^nα_i(\frac{λ_i}{λ_1})^kx_i)$

Dove:
$\lim\limits_{k→+∞}A^kv∼λ_1^kα_1x_1$

Quindi con la seguente successione:
$\begin{cases} u^{(k)}=At^{(k-1)} \\ t^{(k)}=\frac{u^{(k)}}{||u^{(k)}||_∞} \end{cases}$

Dove $u^{(0)}=v$.
Dopo $n$ iterazioni, l'autovettore sarà $t^{(n)}$, e l'autovalore $||u^{(n)}||_∞$ (si può assumere che l'indice maggiore a un certo punto sarà sempre lo stesso).