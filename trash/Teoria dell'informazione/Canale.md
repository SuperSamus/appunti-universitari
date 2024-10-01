Idealmente, un canale senza rumore prende un simbolo in ingresso e fa uscire lo stesso simbolo.

Nella realtà, il rumore può alterare i simboli durante la trasmissione: da un simbolo $x_i$ dell'alfabeto $X$ esce un simbolo $y_j$ dell'alfabeto $Y$.

È necessaria quindi una *codifica di canale*, per minimizzare l'impatto del rumore.

In un *canale discreto senza memoria tempo-invariante*, la probabilità che un $x_i$ diventi un $y_j$ in uscita è nota per ogni $i$ e $j$. Si può quindi rappresentare le varie probabilità in una matrice.

### Entropia congiunta

Date due sorgenti, $X$ e $Y$, con $k$ e $h$ possibili uscite rispettivamente:
$H(X,Y)=-∑\limits_{i=1}^k∑\limits_{j=1}^hp(x_i,y_j)\log p(x_i,y_j)≤H(X)+H(Y)$

La disuguaglianza è dovuta dal [[Informazione#^aae359|lemma del logaritmo]]:
- $H(X)=-∑\limits_{i=1}^kp(x_i)\log p(x_i)=-∑\limits_{i=1}^k(∑\limits_{j=1}^hp(x_i,y_j))\log p(x_i)$
- $H(Y)=-∑\limits_{j=1}^hp(y_j)\log p(y_j)=-∑\limits_{j=1}^h(∑\limits_{i=1}^kp(x_i,y_j))\log p(y_j)$
- $H(X)+H(Y)=-∑\limits_{i=1}^k∑\limits_{j=1}^hp(x_i,y_j)(\log p(x_i)+\log p(y_j))=-∑\limits_{i=1}^k∑\limits_{j=1}^hp(x_i,y_j)\log (p(x_i)p(y_j))$

Quindi, c'è uguaglianza se e solo se $X$ e $Y$ sono indipendenti.

### Entropia condizionata

$H(X|Y)=-∑\limits_{j=1}^hp(y_j)H(X|Y=y_j)=-∑\limits_{i=1}^k∑\limits_{j=1}^hp(x_i,y_j)\log(p(x_i|y_j))$
- $H(X,Y)=H(X)+H(Y|X)$
- $H(X,Y)=H(Y)+H(X|Y)$
- $H(X|Y)≤H(X)$
	- Sono uguali se e solo se $X$ e $Y$ sono indipendenti.

### Informazione mutua

$I(X;Y)=H(X)-H(X|Y)=H(Y)-H(Y|X)=∑\limits_{i=1}^k∑\limits_{j=1}^hp(x_i,y_j)\log\frac{p(x_i,y_j)}{p(x_i)p(y_j)}≥0$

Si definisce *capacità del canale*:
$C_S=\max\limits_{p(x_i)}\{I(X;Y)\}$

Nel cercare di creare una codifica di canale che minimizzi l'impatto del rumore, si vuole massimizzare la capacità del canale:
- Un canale senza rumore ideale ha capacità $\log m$.
- Un canale così rumoroso da essere inutile ha capacità $0$ ($X$ e $Y$ sono indipendenti).