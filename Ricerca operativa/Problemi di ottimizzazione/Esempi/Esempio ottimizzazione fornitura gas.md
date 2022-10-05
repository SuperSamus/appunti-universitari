# Esempio [[Problemi di ottimizzazione|ottimizzazione]] fornitura gas

Bisogna acquistare $L$ milioni di m³ di gas da stoccare. È stato messo a disposizione uno stanziamento da $E$ milioni di euro. $n$ produttori hanno dichiarato le loro tempistiche di fornitura e richieste economiche: il produttore $i$ può fornite $d_i$ milioni di m³ al giorno al prezzo unitario $c_i$ (espresso in milioni di euro).

Quanto gas acquistare da ciascun produttore per minimizzare il tempo complessivo di fornitura (il numero di giorni necessari a ricevere tutti gli $L$ m³ di gas) nel rispetto dello stanziamento disponibile?

- $L$ milioni m³ da acquistare
- $E$ stanziamento disponibile
- $n$ produttori
- $d_i$ milioni m³ gas al giorno
- $c_i$ costo 1 milioni m³

Da trovare:
$x_i$ quanto gas comprare da ciascuno?

Vincoli:
- Vincolo di domanda: $∑\limits_{i=1}^n x_i ≥ L$
- Vincolo di budget: $∑\limits_{i=1}^n x_ic_i ≤ E$
- $x_i ≥ 0 \quad i=1…n$

Funzione obiettivo min: $f(x_1,…,x_n)=\displaystyle\max_{i=1…n} x_i/d_i$

Questa non è una funzione lineare! Non sappiamo risolverla!

## Nuovi vincoli

Creiamo una variabile ausiliaria (approssimazione superiore del valore max cercato):

$t ≥ \displaystyle\max_{i=1…n} x_i/d_i ⟺ t ≥ x_i/d_i \quad i=1…n$

Nuovi vincoli:
- Vincolo di soglia: $t ≥ x_i/d_i \quad i=1…n$

Funzione obiettivo min: $t$

## Aggiunta

L'attivazione del contratto con ciascun produttore ha un costo amministrativo $c$.

Nuove variabili:
- $y_i ∈ \{0,1\}$, $y_i=\begin{cases} 1 &\text{se compro da } i \\ 0 &\text{altrimenti} \end{cases}$

Vincoli cambiati/nuovi:
- Vincolo di budget: $∑\limits_{i=1}^n (x_ic_i+cy_i) ≤ E$
- $x_i ≤ Ly_i$ ($⟺ y_i=0⇒x_i=0$)
	- Sarebbe figo fare $y_i=\begin{cases} 1 &\text{se } x_i>0 \\ 0 &\text{altrimenti} \end{cases}$, ma è una relazione logica, non lineare (idem $x_i > 0⇒y_i=1$)
	- Anche usare $x_iy_i$ nella funzione obiettivo renderebbe la funzione non lineare, perché è quadratica.

## Revisione

Abbiamo un budget infinito che vogliamo minimizzare, e un limite di tempo $D$.

Nuovo vincolo:
- $x_i/d_i ≤ D$

Nuova funzione obiettivo min: $∑\limits_{i=1}^n (x_ic_i+cy_i)$ (che rimpiazza il rispettivo vincolo)
