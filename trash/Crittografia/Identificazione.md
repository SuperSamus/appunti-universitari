Identificazione


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

## MAC

Una funzione pubblica $A(m,k)$ di cui il mittente invia il risultato al destinatario, che riapplica la funzione per vedere se riottiene lo stesso risultato.
Un esempio di funzione è l'[[hash]].