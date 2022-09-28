# Esempio ottimizzazione fornitura gas

Bisogna acquistare $L$ milioni di $m^3$ di gas da stoccare. È stato messo a disposizione uno stanziamento da $E$ milioni di euro. $n$ produttori hanno dichiarato le loro tempistiche di fornitura e richieste economiche: il produttore $i$ può fornite $d_i$ milioni di $m^3$ al giorno al prezzo unitario $c_i$ (espresso in milioni di euro).

Quanto gas acquistare da ciascun produttore per minimizzare il tempo complessivo di fornitura (il numero di giorni necessari a ricevere tutti gli $L$ $m^3$ di gas) nel rispetto dello stanziamento disponibile?

- $L$ milioni $m^3$ da acquistare
- $E$ stanziamento disponibile
- $n$ produttori
- $d_i$ milioni $m^3$ gas al giorno
- $c_i$ costo 1 milioni $m^3$

Da trovare:
$x_i$ quanto gas comprare da ciascuno?

Vincoli:
- Vincolo di domanda: $\displaystyle\sum_{i=1}^n x_i \geq L$
- Vincolo di budget: $\displaystyle\sum_{i=1}^n x_ic_i \leq E$
- $x_i \geq 0 \quad i=1…n$

Funzione obiettivo min: $f(x)=f(x_1,…,x_n)=\displaystyle\max_{i=1…n} x_i/d_i$

Questa non è una funzione lineare! Non sappiamo risolverla!

## Nuovi vincoli

Creiamo una variabile ausiliaria: $t=\displaystyle\sum_{i=1}^n x_i/d_i$ (approssimazione superiore del valore max cercato)

$t \geq \displaystyle\max_{i=1…n} x_i/d_i \iff t \geq \displaystyle\max_{i=1…n} x_i/d_i \quad i=1…n$

Vincoli:
- Vincolo di soglia: $t \geq \displaystyle\max_{i=1…n} x_i/d_i \quad i=1…n$
- Vincolo di domanda: $\displaystyle\sum_{i=1}^n x_i \geq L$
- Vincolo di budget: $\displaystyle\sum_{i=1}^n x_ic_i \leq E$

Funzione obiettivo min: $f(x)=t$

## Aggiunta
L'attivazione del contratto con ciascun produttore ha un costo amministrativo $c$.