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

Motivazione: lanciamo un dado equilibrato, supponiamo di sapere che l'e