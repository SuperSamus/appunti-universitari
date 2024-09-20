Esempi di modelli uniformi
- Estrazioni con ordine con reimmissione (rimpiazzo) di $k$ oggetti da un'urna di $n$ oggetti.
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }n\}=\{1,2,…,n\}×\{1,2,…,n\}×…×\{1,2,…,n\}=\{1,2,…,n\}^k$
  $P$ è uniforme
  $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{n^k}$
- In modo analogo, $k$ lanci di un dado equilibrato
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }\{1,…,6\}\}$
  $P$ è uniforme
  $\#Ω=6^k$

- Estrazioni con ordine senza reimmissione di $k$ oggetti tra $n$ ($k≤n$)
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }n\}=\{w_1,w_2,…,w_k\}|w_i∈\{1,…,n\},w_i \text{ tutti distinti}\}$
  $P$ è uniforme
  $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{n!/(n-k)!}$

- Estrazioni senza ordine senza reimmissione di $k$ oggetti tra $n$ ($k≤n$)
  $Ω=\{C⊆\{1,…,,n\}|\#C=k\}$
  $P$ è uniforme
    $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{\begin{pmatrix}n\\k\end{pmatrix}}\quad (A⊆Ω)$

---

Probabilità condizionata e formula di Bayes

Motivazione: lanciamo un dado equilibrato, supponiamo di sapere che l'esito è un numero pari.
Data questa informazione, vogliamo sapere qual è la probabilità che l'esito sia ≥4: ci aspettiamo $(A=\{4,5,6\},B=\{\text{pari}\})$
$\frac{2}{3}=\frac{\#(A∩B)}{\#B}=\frac{\#(A∩B)/\#Ω}{\#B/\#Ω}=\frac{P(A∩B)}{P(B)}$

Questo è varo in molti casi.

Definizione: Dato $(Ω,𝔉,P)$ spazio di probabilità, $B$ evento non trascurabile (cioè probabilità non nulla), definiamo probabilità condizionata di $A$ dato $B$, con $A$ evento:
$P(A|B)=\frac{P(A∩B)}{P(B)}$

Essa indica la probabilità che accada $A$, sapendo che accade $B$. ($P(A|B)≠P(A∖B)$)

Fatto (TODO, esercizio a casa): fissato $B$ (non trascurabile), $A↦P(A|B)$ è una probabilità su $(Ω,𝔉)$ (mentre $B↦P(A|B)$ non è una probabilità)

Se $A$, $B$ sono eventi, $B$ non trascurabile, $P(A∩B)=P(A|B)P(B)$

Proposizione: Siano $A_1,A_2,…,A_n$ eventi con $A_1∩A_2∩…∩A_n$ non trascurabile. Allora $P(A_1∩A_2∩…∩A_n)=P(A_1)·P(A_2|A_1)·P(A_3|A_1∩A_2)·…·P(A_n|A_1∩…∩A_{n-1})$
Dimostrazione: per induzione su $n$.

Definizione: $B_1,B_2,...,B_n$ eventi formano una partizione di $Ω$ se sono a due a due disgiunti e la loro unione dà $Ω$:
- $B_i∩B_j=∅\quad ∀i≠j$
- $B_1∪B_2∪...∪B_n=Ω$
(Accade uno e uno solo tra gli eventi $B_i$)

TODO: BASTA NON CE LA FACCIO PIÙ
