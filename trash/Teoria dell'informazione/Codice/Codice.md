### Codice

Sistema che associa una sequenza di elementi di $S$ a una sequenza di simboli di un altro alfabeto.
Dato un alfabeto $A$ (con $|A|=d$) e l'insieme delle stringhe $A^*$, si sceglie un insieme di $k$ parole distinte detto *codice*, e si assegna in modo univoco una parola del codice a ogni carattere dell'alfabeto sorgente $Σ$.
Una stringa di $Σ^*$ viene identificata come una sequenza di stringhe $A^*$.

Le parole del codice $C$ hanno lunghezza $\{l_1,l_2,…,l_m\}$. La lunghezza media è:
$L_S(C)=∑\limits_{i=1}^mp_il_i$

Per minimizzare la lunghezza media, i simboli probabili corrispondono a una parola corta mentre i simboli improbabili corrispondono a una parola lunga (si veda [[codice di Huffman]]).
Per il lemma del logaritmo, $H(S)≤L_S(C)$.
- Se sono uguali, il codice è *assolutamente ottimo*
- Se non sono uguali ma $L_S(C)$ è comunque il minimo possibile per $S$, il codice è *ottimo*
- Si può misurare l'*efficienza* di un codice con $\frac{H(S)}{L_S(C)}$
>[!warning]
>La disuguaglianza sopra assume che il logaritmo usato per $H(S)$ sia di base $d$.
>Se invece usa il logaritmo di base $2$, allora $\frac{H(S)}{\log_2(d)}≤L_S(C)$

Se non c'è un carattere separatore, un codice potrebbe essere *ambiguo*. Si vuole che il codice sia *univocamente decifrabile*.
Una soluzione è avere tutte le parole della stessa lunghezza, ma non è desiderabile se i simboli hanno probabilità drasticamente diverse.

>[!info]
>#### Algoritmo di Sardinas-Patterson
>
>Dati gli insiemi $S_0,S_1,…,$ tali che:
>- $S_0=C$
>- $S_i=\{w∈A^*|∃a∈S_0,∃b∈S_{i-1} \text{ t.c. } a=bw∨b=aw\}$
>	- Cioè, l'insieme dei suffissi tra $S_0$ e $S_{i-1}$
>
>Allora condizione necessaria e sufficiente affinché C sia univocamente decifrabile è che
>$∀n>0 \: S_0∩S_n=∅$
>
>L'algoritmo termina con successo in uno dei seguenti casi:
>- $∃i> 0 \: S_i=∅$
>- $∃i,j> 0 \: S_i=S_j$

>[!info]
>#### Diseguaglianza di Kraft-McMillan
>
>Dato un codice lunghezza delle parole $\{l_1,l_2,…,l_m\}$ su un alfabeto di dimensione $d$, per essere univocamente decifrabile è necessario (ma non sufficiente):
>$∑\limits_{i=1}^md^{-l_i}≤1$

Potrebbe comunque essere essere necessario leggere $k$ simboli della parola successiva prima di decodificare il codice. In questo caso, il codice è detto essere con ritardo di decifrazione $k$ (può anche essere illimitato).
Un codice senza questo difetto è *istantaneo*. Un codice istantaneo è univocamente decifrabile.
Condizione necessaria e sufficiente per un codice istantaneo: nessuna parola è *prefisso* di un'altra.
Detto in altro modo, è possibile costruire un albero tale che le parole del codice siano soltanto le foglie.

Se non si possono aggiungere foglie all'albero, il codice è detto *completo*. Ovviamente, un codice ottimo è completo.

### Primo teorema di Shannon

Per codificare un testo $T$ di lunghezza $n→+∞$ prodotto da una sorgente $S$ di entropia $H(S)$, non si possono usare meno di $nH(S)$ bits.

Un testo si può comprimere fino a una lunghezza che corrisponde al suo contenuto di informazione.