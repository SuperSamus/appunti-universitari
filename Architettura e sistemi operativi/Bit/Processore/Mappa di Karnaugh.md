# Mappa di Karnaugh

Alternativa alle tabelle di verità per l'[[Algebra booleana]].

Graficamente può essere di 2, 3 o 4 variabili d'ingresso.

### 2 variabili

Tabella di verità:

| AB  | z   |
| --- | --- |
| 00  | 1   |
| 01  | 1   |
| 10  | 1   |
| 11  | 0   |

Mappa di Karnaugh:

| A\\B | 0   | 1   |
| ---- | --- | --- |
| 0    | 1   | 1   |
| 1    | 1   | 0   |

### 3 variabili

| A\\BC | 00  | 01  | 11  | 10  |
| ----- | --- | --- | --- | --- |
| 0     |     |     |     |     |
| 1     |     |     |     |     |

Dopo 01 viene 11 (invece che 10 come accadrebbe nella tabella di verità) così che cambi una sola variabile.

### 4 variabili

In questa tabella si possono vedere esempi di 2 celle adiacenti che condividono 3 variabili (una sola variabile cambia).

| AB\\CD | 00                                         | 01               | 11               | 10               |
| ------ | ------------------------------------------ | ---------------- | ---------------- | ---------------- |
| 00     | $\bar{B}\bar{C}\bar{D}$ |                  |                  |                  |
| 01     |                                            | $AB\bar{D}$ | $AB\bar{D}$ |                  |
| 11     |                                            |                  |                  | $AC\bar{D}$ |
| 10     | $\bar{B}\bar{C}\bar{D}$ |                  |                  | $AC\bar{D}$ |

Inoltre, cambiare colonna non modifica $AB$, mentre cambiare riga non modifica $CD$:

| AB\\CD | 00   | 01   | 11   | 10   |
| ------ | ---- | ---- | ---- | ---- |
| 00     |      |      |      |      |
| 01     |      |      |      |      |
| 11     | $AB$ | $AB$ | $AB$ | $AB$ |
| 10     |      |      |      |      |

Si può anche vedere "quadrati" dove 2 variabili restano uguali:

| AB\\CD | 00  | 01   | 11   | 10  |
| ------ | --- | ---- | ---- | --- |
| 00     |     | $AD$ | $AD$ |     |
| 01     |     | $AD$ | $AD$ |     |
| 11     |     |      |      |     |
| 10     |     |      |      |     |

O un rettangolo per 1 variabile:

| AB\\CD | 00  | 01  | 11  | 10  |
| ------ | --- | --- | --- | --- |
| 00     |     | $D$ | $D$ |     |
| 01     |     | $D$ | $D$ |     |
| 11     |     | $D$ | $D$ |     |
| 10     |     | $D$ | $D$ |     |

La comodità è, per esempio, se tutte queste celle dove $D=1$ avessero anche $z=1$, allora $z=…+D$.

Infine, tecnicamente c'è anche la cella isolata.

Ciò permette di cancellare variabili dell'espressione di $z$. Il numero di variabili cancellate per ogni "adiacenza" è $\log_2 (\text{\#celle adiacenti})$

Esempio:

![[Mappa di Karnaugh.excalidraw]]

#### Somma

In una somma tra le variabili da 2 bit $X$ ($x_1x_0$) e $Y$ ($y_1y_0$), ricava:
- $z_1$: La prima cifra della somma
- $z_2$: La seconda cifra della somma
- $c$: Se c'è un overflow

Tabella di verità:

| $x_1x_0$ | $y_1y_0$ | $z_1z_0$ | $c$ |
| -------- | -------- | -------- | --- |
| 00       | 00       | 00       | 0   |
|          | 01       | 01       | 0   |
|          | 11       | 11       | 0   |
|          | 10       | 10       | 0   |
| 01       | 00       | 00       | 0   |
|          | 01       | 10       | 0   |
|          | 11       | 00       | 1   |
|          | 10       | 11       | 0   |
| 11       | 00       | 11       | 0   |
|          | 01       | 00       | 1   |
|          | 11       | 10       | 1   |
|          | 10       | 01       | 1   |
| 10       | 00       | 10       | 0   |
|          | 01       | 11       | 0   |
|          | 11       | 01       | 1   |
|          | 10       | 00       | 1   |

Mappe di Karnaugh:

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 1   | 1   |
| 01                 | 0   | 1   | 0   | 1   |
| 11                 | 1   | 0   | 1   | 0   |
| 10                 | 1   | 1   | 0   | 0   |

$z_1=x_1\bar{y_1}\bar{y_0}+x_1\bar{x_0}\bar{y_1}+\bar{x_1}\bar{x_0}y_1+\bar{x_1}y_1\bar{y_0}+\bar{x_1}x_0\bar{y_1}y_0+x_1x_0y_1y_0$

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 1   | 1   | 0   |
| 01                 | 1   | 0   | 0   | 1   |
| 11                 | 1   | 0   | 0   | 1   |
| 10                 | 0   | 1   | 1   | 0   |

$z_0=\bar{x_0}y_0+x_0\bar{y_0}$

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 0   | 0   |
| 01                 | 0   | 0   | 1   | 0   |
| 11                 | 0   | 1   | 1   | 1   |
| 10                 | 0   | 0   | 1   | 1   |

$c=x_1y_1+x_1x_0y_0+x_0y_1y_0$

### Moltiplicazione $2 \times 2$

| $x_1x_0$ | $y_1y_0$ | $z_3z_2z_1z_0$ |
| -------- | -------- | -------------- |
| 00       | 00       | 0000           |
|          | 01       | 0000           |
|          | 11       | 0000           |
|          | 10       | 0000           |
| 01       | 00       | 0000           |
|          | 01       | 0001           |
|          | 11       | 0011           |
|          | 10       | 0010           |
| 11       | 00       | 0000           |
|          | 01       | 0011           |
|          | 11       | 1001           |
|          | 10       | 0110           |
| 10       | 00       | 0000           |
|          | 01       | 0010           |
|          | 11       | 0110           |
|          | 10       | 0100           |

Mappe di Karnaugh:

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 0   | 0   |
| 01                 | 0   | 0   | 0   | 0   |
| 11                 | 0   | 0   | 1   | 0   |
| 10                 | 0   | 0   | 0   | 0   |

$z_3=x_1x_0y_1y_0$

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 0   | 0   |
| 01                 | 0   | 0   | 0   | 0   |
| 11                 | 0   | 0   | 0   | 1   |
| 10                 | 0   | 0   | 1   | 1   |

$z_2=x_1\bar{x_0}y_1+x_1y_1\bar{y_0}$

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 0   | 0   |
| 01                 | 0   | 0   | 1   | 1   |
| 11                 | 0   | 1   | 0   | 1   |
| 10                 | 0   | 1   | 1   | 0   |

$z_1=x_1\bar{x_0}y_0+x_1\bar{y_1}y_0+\bar{x_1}x_0y_1+x_0y_1\bar{y_0}$

| $x_1x_0$\\$y_1y_0$ | 00  | 01  | 11  | 10  |
| ------------------ | --- | --- | --- | --- |
| 00                 | 0   | 0   | 0   | 0   |
| 01                 | 0   | 1   | 1   | 0   |
| 11                 | 0   | 1   | 1   | 0   |
| 10                 | 0   | 0   | 0   | 0   |

$z_0=x_0y_0$

# TODO: quello che ha fatto nella lezione del 30/09