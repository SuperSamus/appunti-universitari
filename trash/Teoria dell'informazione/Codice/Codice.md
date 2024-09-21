# Codice

Sistema che associa una sequenza di elementi di $S$ a una sequenza di simboli di un altro alfabeto.
Dato un alfabeto $A$ (con $|A|=d$) e l'insieme delle stringhe $A^*$, si sceglie un insieme di $k$ parole distinte detto *codice*, e si assegna in modo univoco una parola del codice a ogni carattere dell'alfabeto sorgente $Σ$.
Una stringa di $Σ^*$ viene identificata come una sequenza di stringhe $A^*$.

### Lunghezza media

Le parole del codice $C$ hanno lunghezza $\{l_1,l_2,…,l_m\}$. La lunghezza media è:
$L_S(C)=∑\limits_{i=1}^mp_il_i$

Per minimizzare la lunghezza media, i simboli probabili corrispondono a una parola corta mentre i simboli improbabili corrispondono a una parola lunga (si veda [[Codifiche|codice di Huffman]]).
Per il lemma del logaritmo, $H(S)≤L_S(C)$.
- Se sono uguali, il codice è *assolutamente ottimo*
- Se non sono uguali ma $L_S(C)$ è comunque il minimo possibile per $S$, il codice è *ottimo*
- Si può misurare l'*efficienza* di un codice con $\frac{R}{r_b}=\frac{H(S)}{L_S(C)}$
>[!warning]
>La disuguaglianza sopra assume che il logaritmo usato per $H(S)$ sia di base $d$.
>Se invece usa il logaritmo di base $2$, allora $\frac{H(S)}{\log_2(d)}≤L_S(C)$

#### Dimostrazione (sorgente senza memoria)

Usando il [[Informazione#^aae359|lemma del logaritmo]], e la [[Codice#^134141|somma di Kraft-McMillan]] uguale a 1:
$H(S)=-∑\limits_{i=1}^mp_i\log p_i≤-∑\limits_{i=1}^mp_i\log d^{-l_i}=∑\limits_{i=1}^mp_il_i\log d=L_S(C)\log d$

Si ha quindi un codice assolutamente ottimo se e solo se $∀i\:p_i=d^{-l_i}$.

#### Codifica di Shannon

La codifica di Shannon consiste nell'avere per ogni parola del codice $-\log_d(p_i)≤l_i$.

Anche se il codice non può essere assolutamente ottimo, può però sempre soddisfare:
$H(S)≤L(S)<H(S)+1$.

Dimostrazione:
- $-\log_d(p_i)≤l_i≤⌈-\log_d(p_i)⌉$
	-  $-\log_d(p_i)≤l_i$
	- $d^{-l_i}≤p_i$
	- $∑\limits_{i=1}^md^{-l_i}≤1$
- Moltiplica tutto per $p_i$:
	- $-p_i\log_d(p_i)≤p_il_i≤p_i⌈-\log_d(p_i)⌉≤-p_i\log_d(p_i)+p_i$
- Somma per ogni $i$:
	- $-∑\limits_{i=1}^mp_i\log_d(p_i)≤∑\limits_{i=1}^mp_il_i≤-∑\limits_{i=1}^mp_i\log_d(p_i)+∑\limits_{i=1}^mp_i$
	- Da qui si ottiene la tesi.

Questo però non è ottimo, diversamente dalla [[Codifiche#^d3a9e9|codifica di Huffman]].

>[!info]
>##### Estensione
>Data una sorgente $S'$, che ha gli stessi simboli di $S$ raggruppati in sequenze di lunghezza $n$:
>$H(S')≤L(S')<H(S')+\frac{1}{n}$

## Univocamente decifrabile

Se non c'è un carattere separatore, un codice potrebbe essere *ambiguo*. Si vuole che il codice sia *univocamente decifrabile* (UD).
Possibile soluzione: avere tutte le parole della stessa lunghezza, ma non è desiderabile se i simboli hanno probabilità drasticamente diverse.

>[!info]
>#### Somma di Kraft-McMillan
>
>Dato un codice $C$ con lunghezza delle parole $\{l_1,l_2,…,l_m\}$ e un alfabeto di dimensione $d$:
>$K(C)=∑\limits_{i=1}^md^{-l_i}≤1$
>
> Se la condizione necessaria sopra è necessaria per la possibilità che un codice con queste lunghezze sia istantaneo, mentre per l'esistenza di un codice istantaneo con queste lunghezze è necessaria e sufficiente.
>
>Stesso discorso per un codice *assolutamente ottimo* con:
>$K(C)=1$
>
>Dimostrazione per ottimalità assoluta:
>$H(S)=-∑\limits_{i=1}^mp_i\log p_i≤-∑\limits_{i=1}^mp_i\log \frac{d^{-l_i}}{K(C)}=-∑\limits_{i=1}^mp_i(\log d^{-l_i}-\log K(C))=∑\limits_{i=1}^mp_il_i \log d-\log K(C)=L_S(C)\log d -\log K(C)$
>È quindi necessario che $\log K(C)=0$.

^134141

### Codice istantaneo

Se un codice è istantaneo, cioè si può decifrare senza dover aspettare altri caratteri, allora è UD.

Condizione necessaria e sufficiente: nessuna parola del codice è *prefisso* di un altra.

In un albero che rappresenta la codifica, le parole del codice sono solo in nodi foglia.
Se non si possono aggiungere foglie all'albero, il codice è detto *completo*. Un codice ottimo è completo.

### Codice con ritardo

Se un codice è con ritardo $k$, potrebbe essere necessario leggere $k$ simboli della parola successiva prima di decodificare il codice. (Il ritardo può essere illimitato).
Esempio di ritardo 1, alfabeto sorgente con due simboli, codificati in:
- 0
- 01

>[!info]
>#### Algoritmo di Sardinas-Patterson
>Stabilisce se un codice è univocamente decifrabile.
>
>Dati gli insiemi $S_0,S_1,…,$ tali che:
>- $S_0=C$
>- $S_i=\{w∈A^*|∃a∈S_0,∃b∈S_{i-1} \text{ t.c. } a=bw∨b=aw\}$
>	- Cioè, l'insieme dei suffissi tra $S_0$ e $S_{i-1}$
>
>Allora condizione necessaria e sufficiente affinché C sia univocamente decifrabile è:
>$∀n>0 \: S_0∩S_n=∅$
>
>L'algoritmo termina con successo in uno dei seguenti casi:
>- $∃i> 0 \: S_i=∅$
>- $∃i,j> 0 \: S_i=S_j$

### Primo teorema di Shannon

Per codificare un testo $T$ di lunghezza $n→+∞$ prodotto da una sorgente $S$ di entropia $H(S)$, non si possono usare meno di $nH(S)$ bits.

Un testo si può comprimere fino a una lunghezza che corrisponde al suo contenuto di informazione.
