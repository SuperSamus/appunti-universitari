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
- $\displaystyle\sum_{i=1}^n x_i \geq L$
- $\displaystyle\sum_{i=1}^n x_ic_i \leq E$

Funzione obiettivo min: $f(x)=\displaystyle\sum_{i=1}^n x_i/d_i$
