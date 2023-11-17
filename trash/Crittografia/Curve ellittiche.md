L'[[algebra modulare]] è imprevedibile. Ancora più imprevedibili sono le curve ellittiche. Per quello che ci interessa, sono una curva piana:
$$E(a,b)=\{(x,y)∈ℝ^2:y^2=x^3+ax+b\}$$

In ℝ:
- $4a^3+27b^2≠0$
	- Altrimenti, la cubica avrà radici multiple, oppure la curva avrà cuspidi o nodi in cui la tangente non è definita
- L'elemento neutro è $O$, il *punto all'infinito*
- La curva è simmetrica rispetto all'asse delle ascisse
- Sostituendo $y$ con l'espressione di una retta, si ottiene un'equazione di terzo grado in $x$. Questo vuol dire che una retta può intersecare sulla curva fino a tre volte (si contano anche i punti di intersezione in $ℂ$)
- Dati tre punti disposti su una retta $P$, $Q$, e $R$ ($P≡Q$ per un'intersezione tangente), la somma è definita in modo tale che $P+Q+R=O$
	- Dato che quindi $P+Q=-R$, la somma di $P$ e $Q$ è il punto simmetrico a $R$ rispetto all'asse delle ascisse
	- $x_R=λ^2-x_p-x_Q$
	- $y_R=-y_P+λ(x_P-x_R)$
		- $λ$ è il coefficiente angolare della retta:
			- Se $P≠Q$, allora $λ=\frac{y_Q-y_P}{x_Q-x_P}$
			- Se $P=Q$ (intersezione tangenziale), allora $λ=\frac{3x_P^2+a}{2y_P}$
			- Se $P=-Q$, la loro somma è $O$

Nella crittografia, queste cosa non si fanno in $ℝ$, ma su *campi finiti*:
- $a,b∈ℤ_p\quad p>3$ (dove $p$ è primo, e la *caratteristica* è diversa da 2 o 3)
- $E_p(a,b)=\{(x,y)∈ℤ_p^2:y^2\mod p=x^3+ax+b\mod p\}∪\{O\}$

La "curva" è simmetrica in $\frac{p}{2}$.

L'ordine della curva è il numero dei suoi punti, che può essere al massimo $2p+1$ (i punti $(x,y)$ e $(x,p-y)$ che soddisfano l'equazione, più il punto all'infinito).

Dato un $x$, esiste un $y$ che formano un $(x,y)∈E_p(a,b)$ solo se $x^3+ax+b$ forma un *residuo quadratico* (così da poter ottenere i risultati della radice quadrata di $y^2$). Si può dimostrare che in $\frac{p-1}{2}$ elementi di $ℤ_p$ (escluso $0$) sono residui quadratici.

>[!info]
>#### Teorema di Hasse
>Dato $N$ il numero di punti:
> $|N-(p+1)|≤2{\sqrt{p}}$


### Applicazioni in crittografia

Sono simili agli algoritmi classici (e.g. ElGamal), ma con:
- Prodotto sostituito da somma di punti
- Esponenziazione sostituita da moltiplicazione scalare

#### Moltiplicazione scalare

$Q=kP$

È una funzione one-way trap-door, equivalente al [[Generatore#^865e42|logaritmo discreto]] per l'algebra modulare:
Tempo di esecuzione: $O(\log k$). Come per le potenze %%TODO%%, si può scrivere $k$ come somma di potenze di 2, calcolare in successione i punti $2P,4P,8P,…$, e sommare i punti appropriati.

Trovare $k$ dati $P$ e $Q$ scelti bene invece richiede forza bruta. Non si conoscono metodi migliori.

TODO: Più algoritmi