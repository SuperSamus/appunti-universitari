# Algebra modulare

Dati gli interi $a$, $b$ e $n>0$, $a$ è congruo a $b$ modulo $n$
$$a≡b\mod n$$
se e solo se esiste un intero $k$ tale che:
$$a=kn+b$$

Proprietà:
- $(a + b) \mod m = (a \mod m + b \mod m) \mod m$
- $(a - b) \mod m = (a \mod m - b \mod m) \mod m$
- $(a × b) \mod m = ((a \mod m) × (b \mod m)) \mod m$
- $a^{r × s} \mod m = (a^r \mod m)^s \mod m$

Le operazioni nell'algebra modulare sono "imprevedibili".

## Numeri primi

^bb0f2f

Dato $n∈ℕ$:
- $Z_n=\{0,1,…,n-1\}$
- $Z_n^*⊆Z_n$
	- È l'insieme degli elementi di $Z_n$ coprimi con $n$

Se $n$ non è primo, $Z_n^*$ è computazionalmente difficile da calcolare (bisogna testare tutti i numeri fino a $n$).

**Funzione di Eulero**: $ϕ(n)=|Z_n^*|$
- $n$ primo ⇒ $ϕ(n)=n-1$
- $n$ composto ⇒ $ϕ(n)=n×∏\limits_i^k(1-\frac{1}{p_i})$
	- $p_1,…,p_k$ sono i diversi fattori primi di $n$
	- $n=pq$ ⇒ $ϕ(n)=(p-1)(q-1)$

**Teorema di Eulero**: per $n>1$ e per ogni $a$ co-primo rispetto a $n$: ^5407c3
- $a^{ϕ(n)}≡1\mod n$
	- **Piccolo teorema di Fermat**: Per n primo e per ogni $a∈Z_n^*$:
		- $a^{n-1}≡1\mod n$
	- $a^{-1}=a^{ϕ(n)-1}\mod n$

>[!note]
>L'inverso di $a$ significa $a×a^{-1}≡1\mod n$. Esistenza e unicità dell'inverso sono garantiti se e solo se $a$ e $n$ sono co-primi:
>- $ax≡b\mod n$ ammette soluzione in $x$ se e solo se $MCD(a,n)|b$: in questo caso si hanno esattamente $MCD(a,n)$ soluzioni distinte
>	- Ci deve essere solo una soluzione per ammettere l'inverso, quindi $MCD(a,n)=1$ ⇒ $a$ a $n$ sono co-primi
>
>Affinché l'*anello* di interi $\mod n$ sia un *campo finito* (cioè tutti i numeri non-zero hanno il proprio inverso), è condizione sufficiente che $n$ sia primo

Trovare $a^{-1}$ nel modo sopra è un problema difficile perché occorre conoscere $ϕ(n)$.
Qual è un modo più facile?

### Algoritmo di Euclide

^57f0f6

Algoritmo per il calcolo del $MCD(a, b)$ di due interi $a > 0$, $b ≥ 0,$ con $a ≥ b$
```
Function Euclid
    if (b == 0) return a
    else return Euclid (b, a mod b)
```

Complessità: $O(\log a)$
Esiste la versione estesa per trovare anche $x$ e $y$ nell'equazione $ax+by=MCD(a,b)$

```
Function Extended_Euclid(a,b)
    if (b = 0) return <a, 1, 0>
    else
        <d’, x’, y’> = Extended_Euclid(b, a mod b);
        <d, x, y> = <d', y', x' - ⎣a/b⎦ y'>;
        return <d, x, y>
```
%%Spiegazione su https://www.geeksforgeeks.org/euclidean-algorithms-basic-and-extended/%%
Entrambi gli algoritmi hanno un costo polinomiale.

Quindi:
$$
ax≡1\mod b\\
⇔\\
ax=bz+1
⇔\\
ax+by=MCD(a,b)
$$
Dove $y=-z$ e $MCD(a,b)=1$.

Allora $x=a^{-1}\mod b$  si trova facilmente con l'algoritmo di Euclide esteso.

### Test di Miller-Rabin

^e0c1c1

Come trovare un numero primo?

Dato un potenziale numero primo $N$, trova il più grande $w$ possibile e lo $z$ (dispari) che soddisfano:
$N-1=2^w×z$

Scegli un numero a caso un intero $2≤y≤N-2$.
Per ogni $y$, queste condizioni sono necessarie ma non sufficienti affinché il numero sia primo.
- $MCD(N,y)=1$
- Uno dei due:
	- $y^z\mod N=1$
	- $∃i, 0≤i≤w-1:y^{2^i×z}\mod N=-1$

Se il numero è composto, la probabilità di scegliere un $y$ che comunque soddisfa entrambi i predicati è circa ¼.

Strategia: scegli un $y$ casuale $k$ volte: se tutte le volte i predicati vengono soddisfatti, la probabilità di errore è $<\frac{1}{4^k}$.

Per calcolare efficientemente $y^z\mod N$, ricorda:
 - Scomponi $z$ in $1+2+4+8+…$ (tieni solo quelli rilevanti).
 - $y^{2i}\mod N=(y^i\mod N)^2\mod N$

### Logaritmo discreto

^865e42

Se $n$ non è primo, dato $y=x^z\mod s$, trovare $z$ nella funzione inversa $x=y^{\frac{1}{z}}\mod s$ è difficile. (Miglior algoritmo conosciuto: *index calculus*.)

**Trap door**: se si conosce $v=z^{-1}\mod ϕ(s)$ (chiave segreta), allora $x=y^v\mod s$.
Vedi [[Cifrari asimmetrici#^63a12b|RSA]].