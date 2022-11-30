# Esempio [[Problemi di ottimizzazione|ottimizzazione]] pezzi ferrosi

Vogliamo costruire 1000 pezzi ferrosi da 1 kg ciascuno, che devono possedere:

- Manganese $≥$ 0,45%
- 3,25% $≤$ Silicio $≤$ 5,5%

Ci sono 3 tipi di materiale, tutti i 1000 kg verranno fusi:

|     | A   | B   | C   | Mn  |
| --- | --- | --- | --- | --- |
| % Manganese | 0,45 | 0,5 | 0,4 | 100 |
| % Silicio | 4   | 1   | 0,6 | 0   |
| Costo 1 kg | 25  | 30  | 18  | 10000 |

Dobbiamo produrre i pezzi ferrosi al minor costo possibile. Strutturiamo il problema:

Lo spazio delle soluzioni è composto da 4 valori.

$X=ℝ^4 \quad x=(x_A,x_B,x_C,x_{Mn})$ (variabili quantitative)

Vincoli:

- $x_A+x_B+x_C+x_{Mn}=1000$
- $x_A ≥ 0,x_B ≥ 0,x_C ≥ 0,x_{Mn} ≥ 0$
- $0,45x_A+0,5x_B+0,4x_c+100x_{Mn} ≥ 0,45 * 1000$
- $3,25 ≤ 4x_A+1x_B+0,6x_c+0x_{Mn} ≤ 5,5 * 1000$

Funzione obiettivo: $\min 25x_A+30x_B+18x_c+10000x_{Mn}$

Questo è un problema di **programmazione lineare**.