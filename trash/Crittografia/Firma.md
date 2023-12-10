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
>Problema: un falso $S$ può scegliere $r$ apposta per ottenere qualche informazione su $d$.

### Sign & encrypt

Cifrare il messaggio firmato.

Non fare nell'ordine opposto (cifrare e firmare): sennò chiunque può ottenere la cifratura e metterci la propria firma.

È meglio usare un cifrario simmetrico: con un cifrario asimmetrico si sa solo che ha firmato il messaggio, ma tutti possono mandarlo a chiunque (e chi è il destinatario?).

Per server che mandano ACK, potrebbero decidere di rispondere firmando il messaggio  con la propria chiave e cifrandolo con la chiave pubblica del mittente. Attenzione: non devono farlo per messaggi insensati.
Vogliono dire che un attaccante ha intercettato la cifratura originale per fingersi il mittente (quindi la chiave pubblica della firma che il server userà sarà sbagliata), e con la risposta ricevuta possono risalire al messaggio originale.
Un alternativa è, al posto di avere come firma il messaggio modificato, apporre la firma separatamente.

## MAC

Una funzione pubblica $A(m,k)$ di cui il mittente invia il risultato al destinatario, che riapplica la funzione per vedere se riottiene lo stesso risultato.
Un esempio di funzione è l'[[hash]].

Tutto questo però non protegge da attacchi man-in-the-middle

## Certificato digitale

Gestiti dalle Certification Authorities (CA), infrastrutture che garantiscono la validità delle chiavi pubbliche.

## Schema di firma di ElGamal

^1aa34e

Dato un gruppo ciclico $\mod p$, e un generatore $g$:

- Chiave privata: $x$
	- $2≤x≤p-2$
- Chiave pubblica: $<p,g,y>$
	- $y=g^x\mod p$

**Generazione firma**, svolta dal mittente del messaggio $m$:
- Sceglie un numero casuale $k$ coprimo con $p-1$
- Calcola $r=g^k\mod p$
- Calcola $s=k^{-1}(m-xr)\mod (p-1)$
	- Al posto di $m$ si può usare $H(m)$, con $H$ funzione di [[hash]]
- La firma del messaggio è la coppia $(r,s)$

**Verifica firma**, svolta dal destinatario:
- Calcola $v_1=g^m\mod p$ e $v_2=y^rr^s\mod p$
- Se $v_1=v_2$, accetta la firma

Correttezza:
- $sk\mod(p-1)=(m-xr)\mod(p-1)$
	- $m≡sk+xr\mod(p-1)$
- $v_1=g^m\mod p=g^{sk+xr+t(p-1)}\mod p=g^{sk+xr}(g^{p-1})^t\mod p=g^{sk+xr}\mod p=(g^k)^s(g^x)^r\mod p=r^sy^s\mod p=v_2$
Attenzione: non usare mai lo stesso $k$ per più messaggi. Dati $m$ e $m'$ noti firmati con lo stesso $k$:
- $k=\frac{m-m'}{s-s'}\mod(p-1)$
- $x=\frac{sk-m}{r}\mod(p-1)$
