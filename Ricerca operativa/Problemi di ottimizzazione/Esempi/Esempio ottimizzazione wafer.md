# Esempio [[Problemi di ottimizzazione|ottimizzazione]] wafer

Azienda che produce processori possiede 3000 wafer di silicio. 1 wafer si può usare per:

|                | C      | P      |
| -------------- | ------ | ------ |
| Quantità       | 500    | 300    |
| Resa           | 60%    | 50%    |
| Prezzo         | 200    | 300    |
| Produzione max | 700000 | 400000 |

$X=\mathbb{N}^2$ (*vincolo di interezza*)

- $x_C=$ # processori C prodotti
- $x_P=$ # processori P prodotti

Vincoli:

- $x_C \leq 700000$
- $x_P \leq 400000$
- ${x_C \over 500 * 0,6} + {x_P \over 300 * 0,5} \leq 3000$

Funzione obiettivo max: $200x_C+300x_C$

Si poteva anche fare in un altro modo?

- $w_C=$ # wafer dedicati ai processori C
- $w_P=$ # wafer dedicati ai processori P
- $x_C=500*0.6w_C$
- $x_P=300*0,5w_P$

NO, per via del vincolo di interezza. Il risultato sarebbe stato simile, ma non esattamente uguale.
