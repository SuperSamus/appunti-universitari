# Esempio [[Problemi di ottimizzazione|ottimizzazione]] quartieri città

Una città è costituita da $n$ quartieri. Il direttore dell’azienda sanitaria locale vuole organizzare $m$ presidi sanitari ed assegnare ad essi i quartieri della città. L’assegnamento del quartiere $i$ al presidio $j$ ha un costo $c_{ij}$ e comporta l’assegnamento a tale presidio di tutti gli $a_i$ abitanti del quartiere. Per equilibrare il carico di lavoro dei presidi, il direttore desidera inoltre che il rapporto tra il minimo ed il massimo numero di abitanti assegnati ad un presidio sia almeno pari a $\frac{1}{2}$.
L'azienda sanitaria deve decidere come assegnare i quartieri ai presidi rispettando il vincolo di equilibrio e minimizzando il costo totale di assegnamento. Aiuta il direttore formulando il problema come problema di Programmazione Lineare Intera.

Da trovare:
- $s_{ij} ∈ \{0,1\} \quad s_{ij}=\begin{cases} 1 &\text{se il quartiere } i \text{ viene assegnato al presidio } j \\ 0 &\text{altrimenti} \end{cases}$

Vincoli:
- Ogni quartiere sceglie un presidio: $∑\limits_{j=1}^m s_{ij}=1 \quad i=1…n$
- Vincolo di equilibrio: $∑\limits_{i=1}^n a_is_{ij} \geq \frac{1}{2}∑\limits_{i=1}^n a_is_{ik} \quad j=1…m \quad k=1...m$

Funzione obiettivo: $\min ∑\limits_{i=1}^n∑\limits_{j=1}^m c_{ij}s_{ij}$