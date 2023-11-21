Vedere [[algebra modulare]].

## Generazione numeri pseudocasuali

Ci vuole un algoritmo tale che:
- $Prob(0)=Prob(1)=½$
- La generazione non si può prevedere guardando cosa è uscito in precedenza

L'algoritmo ha:
- Input: seme
	- $s$: Lunghezza del seme
- Output: flusso di bit arbitrariamente lungo
	- $n$: Lunghezza del periodo (a.k.a. *ordine*)
	- La (sotto)sequenza avrà un *periodo*, che si cercherà di avere più lungo possibile ($n>>s$)


Dato che qui ci interessa ottenere sequenze di bit, si consuma $0$ o $1$ a seconda della parità del numero generato.

>[!info]
>### Funzioni one-way
>
>- $x→y=f(x)$ (polinomiale)
>- $y→\text{trovare x t.c }y=f(x)$ (esponenziale)
>
>Si genera quindi una sequenza:
>$x_0→x_1=f(x_0)→x_2=f(x_1)=f^{(2)}(x_0)→…$
>e si consuma al contrario.

### Generatore lineare

$x_i=(ax_{i-1}+b)\mod m$

Il periodo è lungo $m$ se e solo se:
- $MCD(b,m)=1$
- $4|m⇒4|(a-1)$
- $a-1$ deve essere divisibile per tutti i fattori primi di $m$

Affinché $a≠1$ sia possibile, $m$ non può essere un intero privo di quadrati. Questo fatto limita le combinazioni di chiavi possibili.

Generalizzato: $x_i=(a_1x_{i-1}^t+a_2x_{i-1}^{t-1}+a_3x_{i-1}^{t-2}+…+a_{t+1})\mod m$

È lo stesso tipo di trasformazione del *cifrario affine*, che la applica una volta sola. Lì ci vuole che la funzione sia iniettiva, e lo è quando $MCD(a,m)=1$.

### Blum Blum Shub

$x_i=x_{i-1}^2\mod n$

Affinché il periodo sia lungo, ci vuole che:
- $n=p×q$ primi
	- $p$ e $q$ sono $≡3 \mod 4$
	- $GCD(\frac{p-3}{2},\frac{q-3}{2})$ deve essere più basso possibile (preferibilmente $1$)
- $x_0$ è il seme

Per sapere se $p$ e $q$ sono primi, usa il [[trash/Crittografia/Algebra modulare#^e0c1c1|test di Miller-Rabin]].

 ---
 
>[!info]
>### Funzioni one-way trap-door
>
>Funzione la cui inversione è facile solo se si conosce una chiave privata.
>Altrimenti, invertire la funzione è un problema NP hard (non è stato dimostrato che non può essere polinomiale).

### Fattorizzazione numeri primi

^ec9676

Calcolare $n=p×q$ è facile.

Ricostruire $p$ e $q$ a partire da $n$ è difficile, ma non è NP hard.
Oggi, il migliore algoritmo (GNFS) è di tempo $O(2^{\sqrt{b\log b}})$.
Un computer quantistico lo risolve in tempo polinomiale.
Per computer normali, non c'è alcuna dimostrazione che non si possa risolvere in tempo polinomiale (anche se probabilmente non si può).

>[!info]
>Calcolare $ϕ(n)$ è computazionalmente equivalente.

**Trap door**: se si conosce uno dei fattori (la chiave privata), allora ricostruire l'altro è solo una divisione.

### Radice primitiva

^80b90a

$a∈Z_n^*$ è un generatore di $Z_n^*$ (si veda [[Algebra modulare#^bb0f2f|numeri primi]]) se la funzione
$a^k\mod n \qquad 1≤k≤ϕ(n)$
genera tutti e soli gli elementi di $Z_n^*$ (ed è quindi di ordine $ϕ(n)$)

>[!note]
>Per via del teorema di Eulero, $a^k≡1\mod n$ se $k=ϕ(n)$.
>Se succede anche quando $k≠ϕ(n)$, allora $a$ non è un generatore per $n$.

Ci sono degli $n$ per cui non esistono generatori (per esempio 8).

>[!info]
>Se $n$ è primo, avrà $ϕ(n-1)$ generatori.
>$a=1$ non è mai un generatore.
