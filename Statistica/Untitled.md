Esempi di modelli uniformi
- Estrazioni con ordine con reimmissione (rimpiazzo) di $k$ oggetti da un'urna di $n$ oggetti.
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }n\}=\{1,2,...,n\}×\{1,2,...,n\}×...×\{1,2,...,n\}=\{1,2,...,n\}^k$
  $P$ è uniforme
  $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{n^k}$
- In modo analogo, $k$ lanci di un dado equilibrato
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }\{1,...,6\}\}$
  $P$ è uniforme
  $\#Ω=6^k$

- Estrazioni con ordine senza reimmissione di $k$ oggetti tra $n$ ($k≤n$)
  $Ω=\{\text{sequenze ordinate, con ripetizione, di }k\text{ tra }n\}=\{w_1,w_2,...,w_k\}|w_i∈\{1,...,n\},w_i \text{ tutti distinti}\}$
  $P$ è uniforme
  $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{n!/(n-k)!}$

- Estrazioni senza ordine senza reimmissione di $k$ oggetti tra $n$ ($k≤n$)
  $Ω=\{C⊆\{1,...,,n\}|\#C=k\}$
  $P$ è uniforme
    $P(A)=\frac{\#A}{\#Ω}=\frac{\#A}{\begin{pmatrix}n\\k\end{pmatrix}}\quad (A⊆Ω)$

---

Probabilità condizionata e formula di Bayes

Motivazione: lanciamo un dado equilibrato, supponiamo di sapere che l'esito è un numero pari.
Data questa informazione, vogliamo sapere qual è la probabilità che l'esito sia ≥4: ci aspettiamo $(A=\{4,5,6\},B=\{\text{pari}\})$
$\frac{2}{3}=\frac{\#(A∩B)}{\#B}=\frac{\#(A∩B)/\#Ω}{\#B/\#Ω}=\frac{P(A∩B)}{P(B)}$

Questo è varo in molti casi.

Definizione: Dato $(Ω,TODO,P)$ spazio di probabilità, $B$ evento non trascurabile, definiamo probabilità condizionata di $A$ dato $B$, con $A$ evento:
$P(A|B)=\frac{P(A∩B)}{P(B)}$

Essa indica la probabilità che accada $A$, sapendo che accade $B$. ($P(A|B)≠P(A∖B)$)

Fatto (TODO, esercizio a casa): fissato $B$ (non trascurabile), $A↦P(A|B)$ è una probabilità su (Ω,TODO) (mentre $B↦P(A|B)$ non è una probabilità)

Se $A$, $B$