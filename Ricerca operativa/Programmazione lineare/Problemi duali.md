# Problemi duali

Dobbiamo sfamare dei polli al minor costo possibile. Abbiamo le seguenti miscele di mangime:

|            | Proteine | Vitamine | Costo Hg |
| ---------- | -------- | -------- | -------- |
| A1         | 4        | 2        | 120      |
| A2         | 2        | 1        | 75       |
| A3         | 3        | 4        | 95       |
| Fabbisogno | 15       | 3        | /         |

Possiamo quindi dire che abbiamo:
- $A=\begin{bmatrix} 4 & 2 \\ 2 & 1 \\ 3 & 4 \end{bmatrix}$
- $b=\begin{bmatrix} 120 \\ 75 \\ 95 \end{bmatrix}$
- $c=\begin{bmatrix} 15 \\ 3 \end{bmatrix}$

Funzione obiettivo min: $120y_1+75y_2+95y_3$ ($y·b$)

Vincoli ($A^Ty≥c↔yA≥c$):
- $4y_1+2y_2+3y_3≥15$
- $2y_1+y_2+4y_3≥3$

($y≥0$)
- $y_i,y_2,y_3≥0$

È molto lontano dalla [[Programmazione lineare#^03350f|forma canonica]]…

---

Vediamo un altro problema. Siamo un venditore di pillole, e vogliamo convincere l'allevatore a prendere le pillole al posto del mangime. Dobbiamo quindi trovare un prezzo conveniente, ma più profittevole possibile.

- $x_1=$ prezzo di 1 pillola da 1 gr di proteine
- $x_2=$ prezzo di 1 pillola da 1 gr di vitamine

Funzione obiettivo max: $15x_1+3x_2$ (conosciamo il fabbisogno) ($c·x$)

Vincoli (il prezzo deve essere conveniente) ($Ax≤b$):
- $4x_1+2x_2≤120$
- $2x_1+x_2≤75$
- $3x_1+4x_2≤95$
($x≥0$)
- $x_1,x_2≥0$

---

Abbiamo usato lo stesso insieme di dati per entrambi i problemi.

$\min\{y·b:yA≥c∧y≥0\}\quad\max\{c·x:Ax≤b∧x≥0\}$

**Coppia simmetrica** della [[programmazione lineare]].

Il primo ha $m$ variabili e $n$ vincoli. Il secondo ha $n$ variabili e $m$ vincoli.

Proviamo a fare una piccola alterazione ai vincoli del secondo problema. Sapendo che $y≥0$:
- $y_1(4x_1+2x_2)≤120y_1$
- $y_2(2x_1+x_2)≤75y_2$
- $y_3(3x_1+4x_2)≤95y_3$

Sommiamo le disuguaglianze e si ottiene:
$x_1(4y_1+2y_2+3y_3)+x_2(2y_1+y_2+4y_2)≤120y_1+75y_2+95y_3$

Per via dei vincoli del primo problema: $15x_1+3x_2≤…≤120y_1+75y_2+95y_3$

La funzione obiettivo del secondo problema (un $\max$) non vale più della funzione obiettivo del primo problema (un $\min$).

## Coppia asimmetrica della programmazione lineare

$\max\{cx:Ax≤b\}$

Si può scrivere come:
- $x_i=x^+_i-x^-_i$
- $x_i^+,x_i^-≥0$

Cambierà la matrice $A$.