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

Abbiamo usato lo stesso insieme di dati per entrambi i problemi.

## Coppia simmetrica della programmazione lineare

>[!important]
$\min\{y·b:yA≥c∧y≥0\}\quad\max\{c·x:Ax≤b∧x≥0\}$

Il primo ha $m$ variabili e $n$ vincoli. Il secondo ha $n$ variabili e $m$ vincoli.

---

Proviamo a fare una piccola alterazione ai vincoli del secondo problema. Sapendo che $y≥0$:
- $y_1(4x_1+2x_2)≤120y_1$
- $y_2(2x_1+x_2)≤75y_2$
- $y_3(3x_1+4x_2)≤95y_3$

Sommiamo le disuguaglianze e si ottiene:
$x_1(4y_1+2y_2+3y_3)+x_2(2y_1+y_2+4y_2)≤120y_1+75y_2+95y_3$

Per via dei vincoli del primo problema: $15x_1+3x_2≤…≤120y_1+75y_2+95y_3$

La funzione obiettivo del secondo problema (un $\max$) non vale più della funzione obiettivo del primo problema (un $\min$).

Tuttavia si preferirebbe una forma senza vincoli di segno per le variabili:. Esiste un altro formato apposta:

## Coppia asimmetrica della programmazione lineare

>[!important]
$\max\{cx:Ax≤b\}\quad\min\{y·b:yA=c∧y≥0\}$

**(P) problema primale** e **(D) problema duale**

$A∈ℝ^{m×n},b∈ℝ^m,c∈ℝ^n→x∈ℝ^n,y∈ℝ^m$

>[!info]
>Da dove salta fuori il problema duale? Il vincolo $x≥0$ si può replicare con:
>- $x_i=x^+_i-x^-_i$
>- $x_i^+,x_i^-≥0$
>
> Ciò cambierà il problema primale (P) in $\max\{cx^+−cx^−:Ax^+−Ax^−≤b\}$
> 
>e, applicando la definizione di coppia simmetrica, si ottiene il duale (D)
>$\min\{yb:yA≥c,−yA≥−c,y≥0\}$

## Dualità debole

>[!important]
Siano $x∈ℝ^n$ una soluzione ammissibile per (P), e $y∈ℝ^n$ soluzione ammissibile per (D).
Allora $c·x≤y·b$.

Dimostrazione: $c·x=(yA)·x=y·(Ax)≤y·b$

Conseguenze:
- Se (P) è superiormente illimitato, allora (D) è vuoto.
- Se (D) è inferiormente illimitato, allora (P) è vuoto.
>[!important]
>- Sia $\bar{x}∈ℝ^n$ soluzione ammissibile per (P), $\bar{y}∈ℝ^n$ soluzione ammissibile per (D). Se $c·\bar{x}=\bar{y}·b$ allora $\bar{x}$ è una soluzione ottima di (P) e $\bar{y}$ è una soluzione ottima di (D).

Dimostrazione dell'ultimo punto:
- $x$ ammissibile per (P), allora $c·x≤\bar{y}·b=c·\bar{x}$
- $y$ ammissibile per (D), allora $\bar{y}·b=c·\bar{x}≤y·b$

### Esempio

(P)

Funzione obiettivo: $\max 3x_1+2x_2$

Vincoli:
- $x_1-x_2≤1$
- $x_1+x_2≤3$
- $-x_1+x_2≤1$

$\bar{x}=(2,1)$ è soluzione ottima?

- $c=(3,2)$
- $A=\begin{bmatrix}1 & -1 \\ 1 & 1 \\ -1 & 1 \end{bmatrix}$
- $b=\begin{bmatrix}1 \\ 3 \\ 1\end{bmatrix}$

$c·\bar{x}=8$

(D)

Funzione obiettivo: $\min y_1+3y_2+y_3$

Vincoli:
- $\begin{bmatrix} y_1 & y_2 & y_3 \end{bmatrix}A=\begin{bmatrix} c_1 \\ c_2 \end{bmatrix}$
	- $y_1+y_2-y_3=3$
	- $-y_1+y_2+y_3=2$
- $\bar{y}·b=c·\bar{x}$
	- $y_1+3y_2+y_3=8$
- $y_1,y_2,y_3≥0$

Si risolve $y_1=\frac{1}{2},y_2=\frac{5}{2},y_3=0$, che è una soluzione ammissibile.

Quindi $\bar{x}=(2,1)$ è soluzione ottima.






$\bar{x}∈ℝ^n$ ammissibile per (P)$: A\bar{x}≤b$

$ξ∈ℝ^n$ direzione ammissibile per $\bar{x}$ se esiste $\bar{λ}>0$ tale che $\bar{x}+λξ$ è ammissibile per (P). $∀λ∈[0,\bar{λ}$]

$ξ∈ℝ^n$ direzione di crescita per $c·\bar{x}$ se esiste $\bar{λ}>0$ tale che $c·(\bar{x}+λξ)>c·\bar{x}$. $∀λ∈[0,\bar{λ}$]

$c·(\bar{x}+λξ)=c·\bar{x}+λc·ξ>c·\bar{x}↔c-ξ>0$

>[!important]
Sia $\bar{x}∈ℝ^n$ ammissibile per (P). Allora $\bar{x}$ è una soluzione ottima per (P) ⇒ $\bar{x}$ non ammette direzioni ammissibili di crescita.

Dimostrare ⇒ è ovvio.

Dimostrazione ⇐: $\bar{x}$ non ottima: esiste $x∈ℝ^n$ ammissibile per (P) tale che $c·x>c·\bar{x}$.

$ξ=x-\bar{x}→c·ξ=c·(x-\bar{x})=c·x-c·\bar{x}>0$

$\bar{x}+ξ=\bar{x}+λ(x-\bar{x})=(1-λ)\bar{x}+λx$ è ammissibile per $λ∈[0,1]$

$A_i(\bar{x}+λξ)≤b_i$ è veramente ≤?
\=
$A_i\bar{x}+A_iλξ$

$i∈I(\bar{x})$ ovvero $A_i\bar{x}=b_i$

