## Firma digitale

Un utente $U$ si vuole connettere a un servizio $S$. $U$ possiede la sua chiave privata $k_U[priv]$, mentre entrambi conoscono quella pubblica $k_U[pub]$.
I passaggi sono praticamente l'inverso dei [[cifrari asimmetrici]].
- $U$ genera la firma $f=D(m,k_U[priv])$
- $S$ controlla che $C(f,k_U[pub])=m$

Problema: con la firma stai praticamente consegnando il messaggio in chiaro.

>[!info]
>### Esempio:  [[Cifrari asimmetrici#^63a12b|RSA]] inverso
>
>Quando un utente $U$ (che possiede la chiave privata $d$) vuole collegarsi a un servizio $S$ (entrambi conoscono la chiave pubblica $<e,n>$):
>- $S$ genera un numero casuale $r<n$, lo invia a $U$
>- $U$ calcola $f=r^d\mod n$, e lo invia a S
>- Se $f^e\mod n=r$, allora $S$ è sicuro di comunicare con $U$
>
>Problema: un $S$ malvagio può scegliere $r$ apposta per ottenere qualche informazione su $d$.

### Sign & encrypt

Cifrare il messaggio firmato.

Non fare nell'ordine opposto (cifrare e firmare): sennò chiunque può ottenere la cifratura e metterci la propria firma.

È meglio usare un cifrario simmetrico: con un cifrario asimmetrico si sa solo che ha firmato il messaggio, ma tutti possono mandarlo a chiunque (e chi è il destinatario?).

Per server che mandano ACK, potrebbero decidere di rispondere firmando il messaggio con la propria chiave e cifrandolo con la chiave pubblica del mittente.

>[!warning]
Non devono farlo per messaggi insensati.
Vogliono dire che un attaccante ha intercettato la cifratura originale per fingersi il mittente (quindi la chiave pubblica della firma che il server userà sarà sbagliata), e con la risposta ricevuta possono risalire al messaggio originale.

Un alternativa è, al posto di avere come firma il messaggio modificato, apporre la firma separatamente.

## Message Authentication Code (MAC)

Una funzione pubblica $A(m,k)$.

Il mittente e il destinatario concordano a priori un $k$. (Se fatto su un canale insicuro, sono vulnerabili a man-in-the-middle)

Il mittente allega il MAC al messaggio (eventualmente cifrato).
Il destinatario riapplica la funzione: se riottiene lo stesso risultato, allora l'autenticazione ha successo.

Un esempio di funzione è l'[[hash]].
%%Alternativamente si può usare un algoritmo CBC%%

## Certificato digitale

Gestiti dalle Certification Authorities (CA), infrastrutture che garantiscono la validità delle chiavi pubbliche.
Prevengono gli attacchi man-in-the-middle, in quanti le loro chiavi sono conosciute a priori.
TODO

## Schema di firma di ElGamal

^1aa34e

Dato un gruppo ciclico $\mod p$ primo, e un generatore $g$:

- Chiave privata: $x$
	- $2≤x≤p-2$
- Chiave pubblica: $<p,g,y>$
	- $y=g^x\mod p$

**Generazione firma**, svolta dal mittente del messaggio $m$:
- Sceglie un numero casuale $k$ coprimo con $p-1$
	- Altrimenti, $k^{-1}$ non esiste
- Calcola $r=g^k\mod p$
- Calcola $s=k^{-1}(m-xr)\mod (p-1)$
	- Al posto di $m$ si può usare $H(m)$, con $H$ funzione di [[Hash]]
- La firma del messaggio è la coppia $(r,s)$

**Verifica firma**, svolta dal destinatario:
- Calcola $v_1=g^m\mod p$ e $v_2=y^rr^s\mod p$
- Se $v_1=v_2$, accetta la firma

Correttezza:
- $sk\mod(p-1)=(m-xr)\mod(p-1)$
	- $m≡xr+sk\mod(p-1)$
- $v_1=g^m\mod p=g^{xr+sk+t(p-1)}\mod p=g^{xr+sk}(g^{p-1})^t\mod p=g^{xr+sk}\mod p=(g^x)^r(g^k)^s\mod p=y^rr^s\mod p=v_2$
Attenzione: non usare mai lo stesso $k$ per più messaggi. Dati $m$ e $m'$ noti firmati con lo stesso $k$:
- $k=\frac{m-m'}{s-s'}\mod(p-1)$
- $x=\frac{sk-m}{r}\mod(p-1)$

### Digital Signature Algorithm (DSA)

^0d344e

Variante dello schema di firma di ElGamal.
La differenza principale è che $s$ viene calcolato in modo diverso, rendendo i passaggi per la verifica completamente diversi.
%%TODO%%

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

A cosa serve la generazione casuale di $e$? Mettiamo che $P$ non conosce $s$, e fosse sempre $e=1$.
Se $P$ nel passo 1 calcola $u=r^2t^{-1}\mod n$ e nel passo 3 $z=r$, allora $ut\mod n=r^2t^{-1}t\mod n=r^2=z^2\mod n$.
Ma se nel passo 2 $e=0$, allora $P$ si ritrova a dover calcolare $z=\sqrt{u}\mod n=r\sqrt{t^{-1}}\mod n=rs^{-1}\mod n$, e non conoscendo $s$ verrà beccato.
