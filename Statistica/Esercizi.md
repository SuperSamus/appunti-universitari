## Esercizio 1

Una ditta può fare consegne in città o fuori città, urgenti o non urgenti.
Supponiamo di sapere che
- Il 50% delle consegne è urgente
- Il 40% delle consegne è in città
- Il 20% delle consegne è urgente e fuori città

Scelta a caso una consegna, vogliamo calcolare:
a) Probabilità che sia urgente e in città
b) Probabilità che sia urgente o in città
c) Probabilità che sia urgente, sapendo che è in città
d) Se gli eventi urgenti e in città sono indipendenti

Ω={(luogo, tempo)|luogo∈{città,fuori},tempo∈{normale,urgente}}

{urgente}={città,fuori}×{urgente}

P({urgente})=0.5
P({città})=0.4
P({urgente,fuori})=0.2

a) {urgente,città}⊆{urgente}
   P({urgente,città})=P({urgente})-P({urgente,fuori})=0.5-0.2=0.3

b) P({urgente o città})=P({urgente})+P({città})-P({urgente e città})=0.5+0.4-0.3=0.6

c) P({urgente}|{città})=P({urgente e città})/P({città})=0.3/0.4=0.75

d) P({urgente})≠P({urgente}|{città})


Esercizio 2

Da un matto di 40 carte napoletane, se ne estraggono tre, senza rimpiatto (una dopo l'altra).
(Carte napoletane = quattro semi (bastoni, coppe, denari, spade), da 1 a 10 per seme)

S={carte}={1_B,2_B,...,10_B,1_C,2_C,...,10_C,1_D,2_D,...,10_D,1_S,2_S,...,10_S}

a) Probabilità che le prime due carte sinao di denari e l'ultima di coppe?
b) Probabilità che esattamente due carte su tre (in qualunque ordine) siano di denari?

a) Estrazione con ordine senza rimpiazzo:
  Ω={(a_1,a_2,a_3)|a_i∈S,a_i tutti distinti}
  P uniforme
  \#Ω=40*39*38=59280
  A={prime due carte di denari, ultima di coppe}
  \#A=#scelte 1° carta di denari * \#scelte 2° carta di denari * \#scelte 1° carta di coppe=10*9*10=900
  P(A)=#A/#Ω=900/59280

b) Estrazione senza ordine senza rimpiazzo di 3 oggetti su 10
  Ω={C⊆S|#C=3} "C insieme delle carte estratte"
  P uniforme
  $\#Ω=(\begin{pmatrix}40\\3\end{pmatrix})=40!/(3!*37!)=40*39*38/6=9880$
  A={esattamente 2 carte di denari}
  \#A=\# scelte delle 2 carte di denari * \#scelte della carta non di denari=$\begin{pmatrix}10\\2\end{pmatrix}\begin{pmatrix}30\\1\end{pmatrix}$
  $P(A)=\cfrac{\begin{pmatrix}10\\2\end{pmatrix}\begin{pmatrix}30\\1\end{pmatrix}}{\begin{pmatrix}40\\3\end{pmatrix}}=\cfrac{\cfrac{10*9}{2}}{\cfrac{40*39*38}{3*2}}=$
  