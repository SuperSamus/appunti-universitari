## Sistema posizionale

Decimale: 217

| Cifra | Peso |
| --- | --- |
| 7   | $10^0$ |
| 1   | $10^1$ |
| 2   | $10^2$ |

$2*10^2+1*10^1+7*10^0=217$

Binario: 11011001

| Cifra | Peso |
| --- | --- |
| 1   | $2^0$ |
| 0   | $2^1$ |
| 0   | $2^2$ |
| 1   | $2^3$ |
| 1   | $2^4$ |
| 0   | $2^5$ |
| 1   | $2^6$ |
| 1   | $2^7$ |

$1*2^0+0*2^1+0*2^2+1*2^3+1*2^4+0*2^5+1*2^6+1*2^7=217$

| \# bit | Nome |
| --- | --- |
| 8   | byte |
| 4   | nibble |

## Convertire numero

Convertiamo $50_{10}$:

| Valore bit | Totale |
| --- | --- |
| 32 ($2^5$) | 32 (-18) |
| 16 ($2^4$) | 48  |
| 2 ($2^1$) | 50  |

$110010_2$

## Somma

### Decimale

$$
\begin{matrix}
1 & 2 & 3 & + \\
  & 2 & 1 & = \\
1 & 4 & 4
\end{matrix}

$$

### Binaria

$$
\begin{matrix}
0 & 1 & 0 & 1 & + \\
0 & 1 & 0 & 0 & = \\
1 & (1)0 & 0 & 1
\end{matrix}

$$

## Esadecimale

| 1010 | 1110 | 0000 | 0101 |
| --- | --- | --- | --- |
| A   | E   | 0   | 5   |

## Complemento a 2

Se si ha il primo bit che specifica il segno, si ha che abbiamo 2 zeri, e inoltre sono necessaria controlli per vedere se un numero è negativo.

Un modo migliore è invertire tutti i bit e aggiungere 1. Così:

- C'è solo 1 zero
- Puoi sommare i numeri senza preoccuparti di sottrarre se c'è un numero negativo
