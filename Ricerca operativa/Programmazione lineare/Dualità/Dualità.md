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

Funzione obiettivo: $\min 120y_1+75y_2+95y_3$ ($y·b$)

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

Funzione obiettivo: $\max 15x_1+3x_2$ (conosciamo il fabbisogno) ($c·x$)

Vincoli (il prezzo deve essere conveniente) ($Ax≤b$):
- $4x_1+2x_2≤120$
- $2x_1+x_2≤75$
- $3x_1+4x_2≤95$
($x≥0$)
- $x_1,x_2≥0$

Abbiamo usato lo stesso insieme di dati per entrambi i problemi.

## Coppia simmetrica della programmazione lineare

>[!important]
$\min\{y·b:yA≥c,y≥0\}\quad\max\{c·x:Ax≤b,x≥0\}$

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

Tuttavia si preferirebbe una forma senza vincoli di segno per le variabili. Esiste un altro formato apposta:

## Coppia asimmetrica della programmazione lineare

>[!important]
$\max\{cx:Ax≤b\}\quad\min\{y·b:yA=c,y≥0\}$

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

^b4e2a8

>[!important]
Siano $x∈ℝ^n$ una soluzione ammissibile per (P), e $y∈ℝ^n$ soluzione ammissibile per (D).
Allora $c·x≤y·b$.

Dimostrazione: $c·x=(yA)·x=y·(Ax)≤y·b$

Conseguenze:
- Se (P) è superiormente illimitato, allora (D) è vuoto.
- Se (D) è inferiormente illimitato, allora (P) è vuoto.
>[!important]
>- Sia $\bar{x}∈ℝ^n$ soluzione ammissibile per (P), $\bar{y}∈ℝ^n$ soluzione ammissibile per (D).
>Se $c·\bar{x}=\bar{y}·b$ ⇒ $\bar{x}$ è una soluzione ottima di (P) e $\bar{y}$ è una soluzione ottima di (D).

La [[Dualità#^2361d6|dualità forte]] dichiara il ⇐.

Dimostrazione dell'ultimo punto:
- $x$ ammissibile per (P), allora $c·x≤\bar{y}·b=c·\bar{x}$
- $y$ ammissibile per (D), allora $\bar{y}·b=c·\bar{x}≤y·b$

## Crescita

^247330

$\bar{x}∈ℝ^n$ ammissibile per (P) tale che $A\bar{x}≤b$. Mi voglio spostare in un altro punto della regione ammissibile, così che la funzione valga di più.

Introduciamo $ξ∈ℝ^n$:
- *Direzione ammissibile* per $\bar{x}$ se esiste una spostamento massimo $\bar{λ}>0$ tale che $∀λ∈[0,\bar{λ}]\quad \bar{x}+λξ$ è ancora ammissibile per (P).
- *Direzione di crescita* per $c·\bar{x}$ se esiste una spostamento massimo $\bar{λ}>0$ tale che $∀λ∈[0,\bar{λ}]\quad c·(\bar{x}+λξ)>c·\bar{x}$.

$c·(\bar{x}+λξ)=c·\bar{x}+λc·ξ>c·\bar{x}↔c·ξ>0$

In altre parole, l'angolo tra i vettori $c$ e $ξ$ è minore di 90°.

---

>[!important]
Sia $\bar{x}∈ℝ^n$ ammissibile per (P). Allora $\bar{x}$ è una soluzione ottima per (P)
⇔
$\bar{x}$ non ammette direzioni ammissibili di crescita.

Dimostrare ⇒ è ovvio.

Dimostrazione ⇐ per assurdo: supponiamo $\bar{x}$ non ottima, ovvero $∃x∈ℝ^n$ ammissibile per (P) tale che $c·x>c·\bar{x}$.

$ξ=x-\bar{x}→c·ξ=c·(x-\bar{x})=c·x-c·\bar{x}>0$

Per $λ∈[0,1]$, affermo che $\bar{x}+ξ=\bar{x}+λ(x-\bar{x})=(1-λ)\bar{x}+λx$ (cioè la combinazione convessa tra $x$ e $\bar{x}$) è ammissibile.

Da qui, definiamo:

### Direzione ammissibile di crescita

^ff2cae

$A_i(\bar{x}+λξ)\stackrel{?}{≤}b_i$ quale condizioni vanno imposte affinché sia vero?

$A_i(\bar{x}+λξ)=A_i\bar{x}+λA_i·ξ$

Possibili casi, vincolo per vincolo:
- $i∈I(\bar{x})$ ovvero $A_i\bar{x}=b_i$
	- $A_i\bar{x}+λA_i·ξ≤b_i↔A_i·ξ≤0$
- $i∉I(\bar{x})$ ovvero $A_i\bar{x}<b_i$
	- $A_i\bar{x}+λA_i·ξ≤b_i↔λA_i·ξ≤b_i-A_i\bar{x}$ (che è $>0$)
		- Se $A_i·ξ≤0$, ok!
		- Se $A_i·ξ>0$, ok ↔ $λ≤\cfrac{(b_i-A_i\bar{x})}{A_i·ξ}$ (che è $>0$)
		- In entrambi i casi, siamo a posto ($λ$ si può scegliere).

Quindi, i vincoli attivi sono gli unici "problematici".

$ξ∈ℝ^n$ direzione ammissibile per $\bar{x}$ ⇔ $A_i·ξ≤0\quad ∀i∈I(\bar{x})$

>[!important]
>$\bar{x}$ non ammette direzioni ammissibili di crescita
>⇔
>non esiste $ξ∈ℝ^n$ tale che $\begin{cases}A_{I(\bar{x})}ξ≤0 \\ c·ξ>0 \end{cases}$

Di quanto ci si può spostare al massimo $\bar{λ}$?
- $\bar{λ}_i=+∞$ se $A_iξ≤0$
- $\bar{λ}_i=\cfrac{b_i-A_i\bar{x}}{A_iξ}$ se $A_iξ>0$:
- $\bar{λ}=\min\{\bar{λ}_i:i∈N\}$

### Lemma di Farkas (1902)

^15b491

I suoi vari lemmi legano l'impossibilità del risolvere un sistema con la possibilità del risolverne un altro. Qui non si dimostrerà.

Tornando alla possibile crescita di $\bar{x}$:

>[!important]
>$\begin{cases}A_{I(\bar{x})}ξ≤0 \\ c·ξ>0 \end{cases}$ non ha soluzione $ξ∈ℝ^n$ ⇔ $∃y_{I(\bar{x})}:\begin{cases}y_{I(\bar{x})}A_{I(\bar{x})}=c \\ y_{I(\bar{x})}≥0 \end{cases}$

In generale: $c=y_{I(\bar{x})}A_{I(\bar{x})}=∑\limits_{i∈I(\bar{x})}y_iA_i$. In altri termini , $c$ deve far parte dell'[[Programmazione lineare#^15fa21|involucro conico]] generati dai vettori $A_i$.

Questo equivale a rendere uguale a 0 tutti i componenti dove $i∉I(\bar{x})$:

$yA=\begin{bmatrix} y_{I(\bar{x})} & 0 \end{bmatrix}\begin{bmatrix}A_{I(\bar{x})} \\ A_{I(\bar{x})^c}\end{bmatrix}=y_{I(\bar{x})}A_{I(\bar{x})}$

#### Dualità forte

^2361d6

>[!important]
>Supponiamo che (P) e (D) abbiano regioni ammissibili non vuote.
>⇒ $\max\{c·x:Ax≤b\}=\min\{y·b:yA=c,y≥0\}$.

Dichiara il ⇐ della [[Dualità#^b4e2a8|dualità debole]].

Conseguenze:
- Se (P) è superiormente illimitato, allora (D) è vuoto.
- Se (D) è inferiormente illimitato, allora (P) è vuoto.
- (P) ottimo finito ⇔ (D) ha ottimo finito

| (P)\\(D)                 | ottimo finito | inferiormente illimitato | vuoto |
| ------------------------ | ------------- | ---------------------- | ----- |
| ottimo finito            | ✅             | ❌                      | ❌     |
| superiormente illimitato | ❌             | ❌                      | ✅     |
| vuoto                    | ❌             | ✅                      | ✅     |

$c\bar{x}=\bar{y}b↔(\bar{y}A)·\bar{x}=\bar{y}·b↔\bar{y}·b-\bar{y}A\bar{x}=0↔\bar{y}·(b-A\bar{x})=0$

>[!important]
>#### Teorema degli scarti complementari
>Siano $\bar{x}$ una soluzione ammissibile per (P), $\bar{y}$ una soluzione ammissibile per (D):
>$$
>\begin{matrix}\bar{x}\text{ è una soluzione ottima per (P)} \\ \bar{y}\text{ è una soluzione ottima per (D)}\end{matrix}⇔\bar{y}·(b-A\bar{x})=0
>$$

^4e2ee6

$\bar{y}·(b-A\bar{x})=∑\limits_{i=1}^m\bar{y}_i(b_i-A_i\bar{x})=0⇔\bar{y}_i(b_i-A_i\bar{x})=0\quad i=1…m$

Detto in altro modo:
- $A_i\bar{x}<b_i⇒\bar{y}_i=0 \quad i∉I(\bar{x})$
- $\bar{y}_i>0⇒A_i\bar{x}=b_i \quad i∈I(\bar{x})$

## Basi

^e880fd

Rivedi [[Programmazione lineare#^1cbebb|basi]].

$B⊆I(\bar{x})$

### Soluzione primale di base: $\bar{x}=A_B^{-1}b_B$

È possibile che ci siano più vincoli attivi di quanti ne servano per una base.
**Degenere**: $∃i∉B \text{ t.c. }A_i\bar{x}=b_i\quad (i∈I(\bar{x}))$

**Ammissibilità**: $A_N\bar{x}≤b_N$ con $N=\{1,…,n\}∖B$

### **Soluzione duale di base**: $\bar{y}=(\bar{y}_B,\bar{y}_N)$, con:
- $\bar{y}_N=0$
	- Per soddisfare gli [[Dualità#^4e2ee6|scarti complementari]]
- $\bar{y}_B=cA_B^{-1}$
	- Vogliamo che $\bar{y}A=c$
	- In questo modo $(\bar{y}_B,0)\begin{bmatrix}A_B \\ A_N\end{bmatrix}=\bar{y}_BA_B=cA_B^{-1}A_B=c$

**Ammissibilità**: $\bar{y}_B=cA_B^{-1}≥0$
**Degenere**: $∃i∈B \text{ t.c. }\bar{y}_i=0$

>[!important]
Sia $B$ una base. Allora la coppia di soluzione di base $\bar{x}=A_B^{-1}b_B$ e $\bar{y}=(cA_B^{-1},0)$ soddisfano la [[Dualità#^4e2ee6|condizione degli scarti complementari]].

Dimostrazione: $(cA_B^{-1},0)·\begin{bmatrix}b_B-A_B\bar{x} \\ b_N-A_N\bar{x}\end{bmatrix}=cA_B^{-1}(b_B-A_B\bar{x})=cA_B^{-1}b_B-cA_B^{-1}A_B\bar{x}=c\bar{x}-c\bar{x}=0$

>[!warning]
Solo perché la soluzione sembra ottimale, non vuole dire che è ammissibile!

>[!important]
>Sia $\bar{x}∈ℝ^n$ una soluzione primale di base ammissibile. Allora:
>
>$\bar{x}$ è una soluzione ottima di (P)
>⇔
>esiste una base B assoluta a $\bar{x}$ tale che la corrispondente soluzione di base duale $\bar{y}=(cA_B^{-1},0)$ è ammissibile.

>[!important]
>Sia $\bar{y}∈ℝ^n$ una soluzione duale di base ammissibile. Allora:
>
>$\bar{y}$ è una soluzione ottima di (D)
>⇔
>esiste una base B assoluta a $\bar{y}$ tale che la corrispondente soluzione di base primale $\bar{x}=A_B^{-1}b_B$ è ammissibile.

>[!info]
Se la soluzione è non degenere, esiste una soluzione sola. Se invece è degenere, qualche soluzione potrebbe non assere ammissibile, e dobbiamo provarne un'altra.

## Algoritmo del simplesso primale

^7f28a7

Input: $B$ base primale ammissibile

1. $\bar{x}=A_B^{-1}b_B\quad\bar{y}=(cA_B^{-1},0)$
2. Se $\bar{y}_B≥0$, STOP → $\bar{x}$ ottima per (P), $\bar{y}$ ottima per (D)
3. Scegliere $h∈B \text{ t.c. } \bar{y}_h>0$ (indice uscente)
4. $\bar{ξ}=-A_B^{-1}u_{B(h)}$ (direzione di crescita)
5. $\bar{λ}=\min\{\bar{λ}_i:i∈N\}$ (passo) con $\bar{λ}=\begin{cases}\bar{λ}_i=+∞ & \text{se } A_iξ≤0 \\ \bar{λ}_i=\cfrac{b_i-A_i\bar{x}}{A_iξ} & \text{se }A_iξ>0\end{cases}$
6. Se $\bar{λ}=+∞$ (ovvero $A_iξ≤0$), STOP → $\begin{matrix}\text{(P) superiormente illimitato} \\ \text{(D) vuoto}\end{matrix}$
7. Scegliere $k∈N \text{ t.c } \bar{λ}=\bar{λ}_k$ (indice entrante)
8. $B=B∖\{h\}∪\{k\}$ (cambio di base)
9. Ritornare a 1.

Non si può eseguire l'algoritmo nella forma duale. Quello che si fa è convertirlo in forma primale. Trasformare le uguaglianze in disuguaglianze però porterà a una situazione degenere. TODO

La complessità è NP. Esiste un algoritmo polinomiale, ma è estremamente complesso.

L'input è una base primale ammissibile, ma cosa si fa se non ce l'abbiamo?

### Base di partenza

$B$ base$:\bar{x}=A_B^{-1}b_B$

$H=\{i∈N:A_i\bar{x}≤b_i\}\quad J=\{i∈N:A_i\bar{x}>b_i\}$

$\bar{x}$ ammissibile $⇔J=∅$

$v∈ℝ^{|J|}$ (una nuova variabile per ogni vincolo violato da $\bar{x}$)

$\min∑\limits_iv_i$
- $A_B≤b_B$
- $A_H≤b_H$
- $A_Jx-v≤b_J$
- $v≤0$

$B∪J$ è una base ammissibile e $(\bar{x},A_J\bar{x}-b_J)$ la corrispondente soluzione primale.

Dopo l'algoritmo simplesso primale → $(x*,v*)$ soluzione ottima
- $v*≠0⇒$ (P) non ammette soluzioni ammissibili
- $v*=0⇒$ $x^k$ è soluzione ammissibile per (P)

### Regola anticiclo di Bland

Per evitare di riusare le stesse basi.

$h=\min\{i∈B:\bar{y}_i<0\}\quad k=\min\{i∈N:\bar{λ}=\bar{λ}_i\}$

La dimostrazione è complicata (è sugli appunti del prof).