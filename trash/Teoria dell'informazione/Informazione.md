La teoria dell’Informazione ha come oggetto principale di studio la *misurazione*, la *trasmissione* e la *preservazione* dell’informazione emessa da una **sorgente**.
- **Sorgente** (S): emette dati utilizzando un alfabeto $Σ$ (di qualunque natura) di cardinalità $m$.
- **[[Canale]]**: trasmette i dati utilizzando un alfabeto $A$, utilizzando una funzione (di costo $γ$) per trasformare i simboli $σ_i$ (appartenenti a $Σ$) in simboli di $A$ (di solito, $|A|≤|Σ|$)
	- Un **rumore** lo può disturbare. Si può aggiungere *ridondanza* per evitare errori, ma aumenterà il *costo* della trasmissione.
- **Destinatario**: riceve i dati codificati

In una sorgente senza memoria, ogni simbolo $σ_i$ ha una probabilità $P(σ_i)=p_i$ di essere trasmesso ($∑\limits_{i=1}^mp_i=1$)

## **Informazione**

Incertezza associata all'emissione di ciascun simbolo
- $I(σ_i)=\log_b(\frac{1}{p_i})=-\log_b(p_i)$
- Si usa il logaritmo perché:
	- $\log(ab)=\log(a)+\log(b)$
	- $\log(1)=0$ (un evento garantito non fornisce alcuna informazione)

La base del logaritmo determina l'unità di misura dell'informazione:
- $e$: Nat
- $10$: Hartley
- $2$: Bit
	- Se si hanno 2 simboli con probabilità $½$ ciascuno, $I(σ_i)=\log_2(\frac{1}{½})=\log_2(2)=1\text{ bit}$

### Entropia

Data una sorgente, misura l'informazione media per evento.
In una sorgente senza memoria:
$H(S)=∑\limits_{i=1}^mp_iI(σ_i)=∑\limits_{i=1}^mp_i\log_b(\frac{1}{p_i})=-∑\limits_{i=1}^mp_i\log_b(p_i)$

>[!note]
>#### Lemma del logaritmo
>Date due distribuzioni di probabilità $\{p_1,p_2,…,p_m\}$ e $\{q_1,q_2,…,q_m\}$ , con $∑\limits_{i=1}^mp_i=1$ e $∑\limits_{i=1}^mq_i=1$, vale:
>$$-∑\limits_{i=1}^mp_i\log_bp_i≤-∑\limits_{i=1}^mp_i\log_bq_i$$

^aae359

Usando il lemma, $H(S)=-∑\limits_{i=1}^mp_i\log(p_i)≤-∑\limits_{i=1}^mp_i\log(\frac{1}{m})=-\log(\frac{1}{m})∑\limits_{i=1}^mp_i=\log m$

Quindi, $0≤H(S)≤\log m$ (l'upper limit è raggiunto se i simboli sono equiprobabili).

#### Notazioni

^4a0ca6

- $r$ symbol rate (symboli/sec)
	- È la quantità di simboli dell'alfabeto sorgente trasmessi al secondo.
- $R$ information rate (bit/sec)
- $r_b$ signaling rate (bitnit/sec)
	- Detto anche *bitrate*, è la quantità di simboli binari (dopo la codifica della sorgente) trasmessi al secondo.

Entropia dell'alfabeto sorgente: $H(S)$
$R=rH(S)≤r\log(m)$

Entropia della codifica binaria: $Ω(p)≤1$
$R=rH(S)=r_bΩ(p)≤r_b$

#### Modelli markoviani

^87a4de

(Vedere [[Canale#^48225d|Entropia condizionata]])

La formula precedente per l'entropia assume che la sorgente $S$ sia senza memoria. La vera formula è:
$H(S)=\lim\limits_{n→∞}\frac{1}{n}H(X_1,…,X_n)=\lim\limits_{n→∞}\frac{1}{n}∑\limits_{\overrightarrow{a}∈Σ^{(n)}}p(\overrightarrow{a})\log (p(\overrightarrow{a}))$
dove $Σ^{(n)}$ rappresenta l’insieme di stringhe formate da $n$ simboli dell'alfabeto $Σ$ e $p(\overrightarrow{a})$, con $\overrightarrow{a}∈Σ^{(n)}$, rappresenta la probabilità che $n$ simboli consecutivi emessi da $S$ siano uguali a $\overrightarrow{a}$.

Alternativamente: $H(S)=H(X_n|X_{n-1},…,X_0)$

Una formula del genere è difficile da calcolare nella realtà per via del limite verso l'infinito.

Per un *modello markoviano* di ordine $k$, si intendono le sorgenti dove le probabilità dei simboli dipendono dai $k$ simboli che lo hanno preceduto:
$H_k(S)=∑\limits_{\overrightarrow{a}∈Σ^{(k)}}p(\overrightarrow{a})H(S|\overrightarrow{a})$

### Teoremi di Shannon

#### Primo

(Vedere [[Codice#^1c7957|Lunghezza media]])

Per codificare un testo $T$ di lunghezza $n$ prodotto da una sorgente $S$ di entropia $H(S)$, non si possono usare meno di $nH(S)$ bits.

Un testo si può comprimere fino a una lunghezza che corrisponde al suo contenuto di informazione.

$L(S)≥H(S)$

#### Secondo

(Vedere [[Canale#^dd30fc|informazione mutua]])

Esiste un sistema di codifica tale che la probabilità di errore sia arbitrariamente piccola se e solo se $R<C$.

Se $R>C$, è impossibile trasmettere informazione senza errori in modo affidabile.
