Alice a Bob, due che non si sono mai visti prima, hanno bisogno di comunicare.
Per comunicare in modo sicuro hanno bisogno di una chiave crittografica, ma come se la scambiano?

#### Trusted Third Party

Un'entità che conosce sia Alice che Bob, e ha già una chiave di comunicazione per ciascuno.
Può quindi generare e inviarli una chiave per comunicare tra loro.
Problemi: questa entità deve essere sempre online. Inoltre, bisogna fidarsi di un'entità di natura inaffidabile, e anche nel caso la fiducia fosse meritata, resta un punto di errore per tutto quelli di cui si sono fidati.

## Cifrari asimmetrici

Permette a tutti di inviare messaggi cifrati, ma solo il ricevente li può decifrare.
Usa due chiavi diverse:
- $k_{pub}$ per cifrare, *pubblica*
- $k_{priv}$ per decifrare, *privata*, nota solo al destinatario

Per ogni utente che vuole essere destinatario, esiste una coppia $<k_{pub},k_{priv}>$

Funzione di cifratura: $c=C(m,k_{pub})$
Funzione di decifrazione: $m=D(c,k_{priv})$

È *facile* dalla chiave privata generare quella privata, ma è *difficile* dalla chiave pubblica generare quella privata.

Difetto: è vulnerabile al chosen plain-text attack.

### RSA

^63a12b

Vedere [[Generatore#^ec9676|fattorizzazione numeri primi]].

Chiave pubblica: $<e,n>$
Chiave privata: $d$

$c=m^e\mod n$
$m=c^d\mod n$

Per massimizzare la difficoltà (e impedire attacchi brute-force):
- $p$ e $q$ devono essere molto grandi (almeno 1024 bit)
- $p$ e $q$ non devono essere troppo vicini tra loro (cioè vicini a $\sqrt{n}$)
- $p-1$ e $q-1$ devono contenere un fattore primo grande
- $GCD(p-1,q-1)$ deve essere piccolo (idealmente 2)
- Non condividere fattori primi con altri moduli
	- Per esempio, non usare 253 se hai usato 341: $GCD(253,341)=11$, che è un fattore per entrambi

Finalmente si sceglie la $e$. È necessario che:
- $MCD(e,ϕ(n))=1$
- $e$ sia grosso, per evitare:
	- $m^e<n$
	- Che venga scelto identico tra diversi utenti.
%%
Se dovesse succedere che con lo stesso $e$ venga cifrato lo stesso messaggio:
		- Abbiamo $c_i=m^e\mod n_i$ per $1≤i≤e$
			- Assumiamo che $m<n_i$ e che i vari $n_i$ siano primi tra loro
		- Per via del teorema cinese del resto, esiste (ed è calcolabile in tempo polinomiale) un unico $m'<n=∏n_i$ che soddisfa $m'≡m^e\mod n$.
			- Dato che $m^e<n$, allora $m'=m^e$, e una semplice radice trova $m$.
%%

Calcola $d=e^{-1}\mod ϕ(n)$

Dimostrazione che $D(C(m, e), d)=m$, cioè che $c^d\mod n=(m^e\mod n)^d=m^{ed}\mod n=m$:
- Se $p$ e $q$ non dividono $m$ (quindi $n$ è coprimo a $m$):
	- $ed≡1\mod ϕ(n)=1+kϕ(n) \quad k∈ℕ$
	- $m^{ed}\mod n=m^{1+kϕ(n)}\mod n=m(m^{ϕ(n)})^k\mod n=m×1^k\mod n=m$
- Se $p|m$ (quindi $MCD(m,n)=p$)
	- Per $\mod p$:
		- $m≡0\mod p≡m^k \quad k∈ℕ$
		- $m^{ed}≡0\mod p⇒m^{ed}-m≡0\mod p$
	- Per $\mod q$:
		- $m^{ed}\mod q=m^{1+kϕ(n)}\mod q=m(m^{ϕ(n)})^k\mod q=m(m^{(p-1)(q-1)})^k\mod q=m(m^{ϕ(q)})^{(p-1)k}\mod q=m×1^{(p-1)k}\mod q=m\mod q$
	- $\begin{rcases}m^{ed}-m≡0\mod p \\ m^{ed}-m≡0\mod q\end{rcases}⇒m^{ed}-m≡0\mod pq=m^{ed}-m≡0\mod n$
		- E dato che $m<n$, allora $m^{ed}\mod n=m\mod n=m$

%%
Attacco a tempo: più grande è $d$, più tempo ci vuole a decifrare il messaggio. Un attaccante può stimare $d$ a seconda della velocità con cui i due utenti comunicano.
%%

### Cifrario di ElGamal

^2ac74b

Viene svolto in tre fasi.

**Generazione chiavi**, svolta dal destinatario, usando il metodo di **Diffie-Hellman**:
- Dato un gruppo ciclico $\mod p$, viene scelto un generatore $g$ (il cui ordine si rappresenta con $n$) e un numero casuale $x∈\{1,…,n-1\}$
	- Preferibilmente, si vuole che $g$ sia una [[Generatore#^80b90a|radice primitiva]]
- Calcola $h=g^x\mod p$
- Chiave pubblica: $<p,h,g,n>$, chiave privata: $x$

**Cifratura**, svolta dal mittente del messaggio $m$:
- Sceglie un numero casuale $y∈\{1,…,m-1\}$
- Calcola il *segreto condiviso* $s=h^y\mod p$
- Calcola le cifrature e le invia al destinatario:
	- $c_1=g^y\mod p$
	- $c_2=m×s\mod p$

**Decifrazione**, svolta dal destinatario:
- Calcola $s=c_1^x\mod p$
	- $c_1^x=g^{xy}=h^y$
- Calcola $m=c_2×s^{-1}\mod p$

Un attaccante ha bisogno di ricostruire $s$, e per farlo deve trovare $x$ o $y$ con il logaritmo discreto, che è difficile.

Debolezze, che un attaccante può sfruttare:
- Man-in-the-middle: se non si può conoscere $x$ o $y$, ma si può manipolare i messaggi per la via, allora ci si può inventare uno $z$
	- Intercetta il destinatario, si inventa uno $z$, e invia al mittente un falso $h_{fake}=g^z$
	- Intercetta il mittente e calcola $s_{mitt}$ e $m$ con i passaggi di decifrazione
	- Calcola $s_{dest}=h_{real}^z$ per cifrare $m$ e inviare $c_1$ e $c_2$ al destinatario, così che non si accorga di niente
- Se per qualche motivo conosce un $m$, può calcolare facilmente il segreto condiviso, e sfruttarlo per i messaggi futuri: $s=c_2×m^{-1}\mod q$
	- Per aggirare il problema, i comunicante generano le chiavi di continuo
