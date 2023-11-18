## Firma

### [[Cifrari asimmetrici#^63a12b|RSA]] inverso

Quando un utente $U$ (che possiede la chiave privata $d$) vuole collegarsi a un servizio $S$ (entrambi conoscono la chiave pubblica $<e,n>$):
- $S$ genera un numero casuale $r<n$, lo invia a $U$
- $U$ calcola $f=r^d\mod n$, e lo invia a S
- Se $f^e\mod n=r$, allora $S$ è sicuro di comunicare con $U$

Problema: un falso $S$ può scegliere $r$ apposta per ottenere qualche informazione su $d$.