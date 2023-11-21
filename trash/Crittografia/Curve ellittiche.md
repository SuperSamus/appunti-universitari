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

Esistono algoritmi (come quello di Schoof) che permettono di trovare in tempo polinomiale quali sono i punti della curva.

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

È una funzione one-way trap-door, equivalente al [[Algebra modulare#^865e42|logaritmo discreto]] per l'algebra modulare:
Tempo di esecuzione: $O(\log k$). Come per le potenze %%TODO%%, si può scrivere $k$ come somma di potenze di 2, calcolare in successione i punti $2P,4P,8P,…$, e sommare i punti appropriati.

Il miglior algoritmo conosciuto per trovare $k$ dati $P$ e $Q$ scelti bene (Pollard ρ) è molto peggio rispetto all'index calculus (per la normale algebra modulare), il che rende le curve ellittiche più sicure.

Il numero $n$ più basso tale che $nP=O$ è l'*ordine* del punto.

#### [[Cifrari asimmetrici#^2ac74b|ElGamal]] ellittico

**Generazione chiavi**, svolta dal destinatario:
- Si ha una curva ellittica $E_p(a,b)$ e un punto $P$ della curva di ordine $n$ alto
- Sceglie a caso $x<n$
- Calcola $Y=xP$
- Chiave pubblica: $<Y,P,<p,a,b>,n>$, chiave privata: $x$

**Cifratura**, svolta dal mittente del messaggio $m$:
- Usa una funzione invertibile (pubblica) $f:m↦P_m$ per ottenere $P_m$
- Sceglie un numero casuale $k<n$
- Calcola le cifrature e le invia al destinatario:
	- $c_1=kP$
	- $c_2=kY+P_m$

**Decifrazione**, svolta dal destinatario:
- Calcola $P_m=c_2-xc_1$
	- $k(xP)+P_m-x(kP)$
- Calcola $m=f^{-1}(P_m)$

Un attaccante ha bisogno di trovare $x$ (e decifrare come farebbe il destinatario) o $k$ ($P_m=c_2-kY$), ma per farlo deve usare il logaritmo discreto, che è difficile.

Un esempio di $f(m)$ sarebbe il punto $(m,\sqrt{m^3+ax+b})$, ma c'è circa il 50% di probabilità che questo non sia un punto valido.
Alternativa: scegliere un $h$ (pubblico) tale che $(m+1)h<p$, e:
```
for i=0 to h-1 {
  x = m * h + i;
  y = sqrt(x^3 + a*x + b);
  if is_int(y) {
    return (x, y);
  }
}
failure!
```

Probabilità di successo: circa $1-(\frac{1}{2})^h$
$f^{-1}(x)=⌊\frac{x}{h}⌋$

### Elliptic Curve [[Firma|Digital Signature]] Algorithm

Variante del DSA, a sua volta variante dello [[Firma#^1aa34e|schema di firma di ElGamal]].

**Generazione chiavi**:
- Si ha una curva ellittica $E_p(a,b)$ e un punto $P$ della curva di ordine $n$ alto e primo
- Sceglie a caso $x<n$
- Calcola $Q=xP$
- Chiave pubblica: $<Q,P,<p,a,b>,n>$, chiave privata: $x$

**Generazione firma**, svolta dal mittente del messaggio $m$:
- Sceglie un numero casuale $k<n$
- Calcola il punto $R=kP$, e dato $R_x$ la coordinata dell'ascisse, poni $r=R_x\mod n$
	- Se $r=0$, riprova con un altro $k$
- Calcola $e=H(m)$, con $H$ funzione di [[hash]]
- Calcola $s=k^{-1}(e+xr)\mod n$
	- Se $s=0$, riprova da capo con un altro $k$
- La firma del messaggio è la coppia $(r,s)$

**Verifica firma**, svolta dal destinatario:
- Calcola $e=H(m)$
- Calcola $w=s^{-1}\mod n$
- Calcola $u_1=ew$ e $u_2=rw$
- Calcola il punto $X=u_1P+u_2Q$
	- Se $X=O$, rifiuta la firma
- Calcola $v=X_x\mod n$
- Se $v=r$, accetta la firma

Correttezza:
- $k=s^{-1}(e+xr)\mod n=w(e+xr)\mod n=(we+wxr)\mod n=(u_1+xu_2)\mod n$
- $X=u_1P+u_2Q=u_1PB+u_2xP=(u_1+u_2x)P=kP=R$
	- $r=R_x\mod n$
	- $v=X_x\mod n$

Attenzione: non usare mai lo stesso $k$ per più messaggi. Dati $m$ e $m'$ noti firmati con lo stesso $k$:
- $k=\frac{e-e'}{s-s'}\mod n$
- $x=\frac{sk-e}{r}\mod n$

## Protocollo a conoscenza zero

Permette a un "provatore" $P$ di (Peggy) dimostrare a un verificatore $V$ (Victor) di conoscere un fatto, senza però rivelargli il fatto stesso. (Per esempio, per farsi pagare primo di rivelarlo.)

Un esempio di fatto è conoscere l'$x$ che soddisfa $y=g^x\mod n$.

I vari algoritmi non sono perfetti: per ogni volta che vengono ripetuti, c'è una probabilità per cui $P$ può comunque avere successo senza sapere niente, quindi vengono ripetuti più volte per ridurre la probabilità.

### Euristica di Fiat–Shamir

Esempio: Peggy vuole a dimostrare a Victor di conoscere $s=\sqrt{t}\mod n$ (con $n=pq$).

Dati $t$ e $n$ pubblici:
1. $P$ genera casualmente $r<n$, calcola $u=r^2\mod n$, e invia $u$ a $V$
2. $V$ genera casualmente $e∈\{0,1\}$ e lo invia a $P$
3. $P$ calcola $z=rs^e\mod n$ e lo invia a $V$
4. Se $z^2\mod n$ è diverso da $ut^e\mod n$, allora $P$ è un bugiardo
	- $z^2=r^2(s^2)^e=ut^e$

In teoria, $P$ potrebbe ingannare $u$ calcolando nel primo passo