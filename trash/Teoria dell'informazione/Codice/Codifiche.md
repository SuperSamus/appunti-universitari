### Codice di Shannon-Fano

Per costruire il codice, i simboli vengono divisi in 2 gruppi tali che la somma delle probabilità siano quasi identiche. Per i simboli del primo gruppo il codice comincerà con $0$, mentre nel secondo gruppo con $1$.
Il processo viene ripetuto, finché i "gruppi" non saranno composti da un solo simbolo.

Non è ottimale.

### Codice di Huffman

^d3a9e9

Un codice specifico a una determinata sorgente $S$ per minimizzarne la lunghezza.
L'albero binario corrispondente è chiamato *albero di Huffman*.

Ottenendo le probabilità dei vari simboli, supponiamo $p_1≥p_2≥…≥p_m$.
Sia $C$ un codice prefisso ottimo per $S$ tale che $c_i$ è la parola di codice associale al simbolo $σ_i$.
- Se $p_j≥p_k$, allora $|c_j|≤|c_k|$
- $|c_m|=|c_{m-1}|$
	- I due simboli meno probabili hanno la stessa lunghezza (uno finisce con $0$, l'altro con $1$).

Data $\text{Huff}(S)$ la lunghezza media del codice di Huffman per $S$: $H(S)≤\text{Huff}(S)<∑\limits_{i=1}^mp_i⌈-\log p_i⌉$

>[!warning]
>È possibile che ci siano diversi simboli con una identità bassa probabilità. In tal caso, si può scegliere qualunque.
>Questo vuol dire che la lunghezza di ogni parola del codice può essere diversa, a seconda di cosa viene scelto.
>In un implementazione reale, è meglio minimizzare la varianza.

#### Algoritmo di Huffman

Permette di ottenere codici binari da un alfabeto.

- Indichiamo con $R(S)$ la sorgente ridotta: i due simboli meno probabili sono sostituiti da simbolo che ha probabilità $p_m+p_{m-1}$.
- Sia $C_R$ il codice prefisso per $R(S)$, in cui $z$ è la parola associata al simbolo sostitutivo. Se il codice $C$ usa per quei due simboli originali le parole $z+'0'$ e $z+'1'$, e per il resto le stesse di $C_R$, allora $C$ è codice prefisso.
	- $L_S(C)=L_{R(S)}(C_R)+p_m+p_{m-1}$
		- Viene sommata la possibilità che si aggiunga una lettera rispetto al codice ridotto.
	- Se $C_R$ è ottimale, allora anche $C$ è ottimale.

Si costruisce quindi una successione di sorgenti finché non si arriva a una sorgente con soli due simboli.

#### Codifica congiunta

^4dbc8d

Nonostante il codice di Huffman sia ottimo, non è assolutamente ottimo. A volte la differenza è piccola, ma non sempre.
Per esempio:

| $S$ | $P$ | $I(σ_i)=-\log(p_i)$ |
| --- | --- | ------------------- |
| 0   | 0.1 | 3.322               |
| 1   | 0.9 | 0.152               |

L'informazione del simbolo $1$ è molto bassa, però ci serve comunque 1 bit intero per rappresentarla: si sprecano $1-0.152=0.848$.
Soluzione: codifica congiunta.

| $S^2$ | $P$  | $I(σ_i)=-\log(p_i)$ |
| ----- | ---- | ------------------- |
| 00    | 0.01 | 6.644               |
| 01    | 0.09 | 3.474               |
| 10    | 0.09 | 3.474               |
| 11    | 0.81 | 0.304               |

Qui non solo lo spreco viene ridotto a $1-0.304=0.696$, ma dato che si sta rappresentando 2 bit (con una codifica che userà 1 bit in questa caso), il vero spreco è ulteriormente dimezzato a $0.348$.

Volendo, si può usare codificare sequenze di simboli di lunghezza arbitraria (*parole*). Tuttavia, per un testo, scegliere un *dizionario* che pesi poco a comprima tanto (cioè, che massimizzi la compressione) è un problema difficile.

### Codifica aritmetica

Trasforma una stringa di simboli in un singolo numero appartenente a $[0,1)$.
Risulta migliore rispetto alle codifiche di Huffman in casi di distribuzioni asimmetriche. È sempre *quasi ottima*.
Dato $Aritm(S)$ la lunghezza media per simbolo di $S$, e $n$ la lunghezza della stringa: $H(S)≤Aritm(S)<H(S)+\frac{2}{n}$.
Quindi, una stringa molto lunga avrà una codifica vicinissima all'entropia.

Purtroppo, il dover usare aritmetica a precisione limitata non lo rende un granché nella pratica.

Algoritmo di codifica:
1. Imposta un intervallo globale a $[0,1)$
2. Fai una tabella che partiziona i simboli della stringa nell'intervallo globale: occupano una percentuale di spazio pari alla loro probabilità
3. Prendi il simbolo dalla stringa da codificare: imposta l'intervallo globale a quello del simbolo
4. Se ci sono altri simboli vai al punto 2, altrimenti il risultato è un numero che fa parte dell'intervallo globale attuale.

Esempio (in decimale):

| Simbolo | Probabilità |
| ------- | ----------- |
| A       | 0.5         |
| B       | 0.33        |
| C       | 0.17        |

Gli intervalli per i simboli (originale) quindi saranno:

| Simbolo | Intervallo   |
| ------- | ------------ |
| A       | $[0,0.5)$    |
| B       | $[0.5,0.83)$ |
| C       | $[0.83,1)$             |

Se il prossimo simbolo della stringa è B, il nuovo intervallo globale sarà $[0.5,0.83)$ e si ripartiziona la tabella:

| Simbolo | Intervallo       |
| ------- | ---------------- |
| A       | $[0.5,0.665)$    |
| B       | $[0.665,0.7739)$ |
| C       | $[0.7739,0.83)$  |

Per un carattere $X$:
$NewHigh(X):=GlobalLow+(GlobalHigh−GlobalLow)×OriginalHigh(X);$
$NewLow(X):=GlobalLow+(GlobalHigh−GlobalLow)×OriginalLow(X);$

Nella decodifica, se le probabilità sono molto sbilanciate, c'è il rischio di non sapere quando smettere. È quindi necessario aggiungere un carattere EOF nella codifica.

### Trasformazione Burrows-Wheeler (BWT)

- Si parte da un testo $T$
- Si crea una matrice $n×n$, con $|T|=n$ che consiste in $T$ ruotato in tutti gli $n$ modi possibili
- Si ordine (per righe) la matrice in ordine alfabetico
- La prima colonna viene chiamata $F$, l'ultima colonna viene chiamata $L$

Le proprietà di $L$ sono:
- È facilmente comprimibile TODO Perché? Parola bilanciata.
- Ordinandolo in modo stabile, si ottiene $F$
- Preso un carattere da $L$ e mappandolo al corrispondente $F[i]$, allora $L[i]$ è il carattere precedente in $T$

Questo significa che dato $L$ e l'ultimo carattere di $T$, è possibile ricostruire tutto $T$.
Questo algoritmo di decompressione è lineare, ma è poco cache-friendly e quindi lento.
Bzip2 si basa sul BWT.

#### Suffix array

Una struttura dati per l'indexing: prende tutti i suffissi di $|T|$, insieme al loro indice, e li ordina in ordine alfabetico. Il suffix array è il primo carattere per suffisso (chiave) con il rispettivo indice (valore).
Se si vuole quindi cercare un pattern $P$, basterà fare una ricerca binaria, e si otterrà gli indici del primo carattere del pattern. In tempo $O(\log(|T|)|P|)$ si trovano tutti i pattern.

Problema: questa struttura è pesante, dati che gli indici pesano (almeno) 4 byte, in confronto al (di solito) singolo byte del carattere. Si moltiplica lo spazio usato per 5!
Soluzione: con il BWT si ha una struttura compressa $L$ da cui si può ottenere i suffissi ordinati $F$. Anche se non ritorna gli indici, permette comunque di ottenere il testo intorno al pattern.

### Distance coding (DC)

Una codifica che per ogni parola d'ingresso, emette la distanza dalla precedente occorrenza dello stesso simbolo (se è la prima volta che compare, assumi che il testo sia cominciato digitando ordinatamente l'alfabeto).
Difetto: è possibile che la distanza sia maggiore del numero di simboli dell'alfabeto

#### Move-to-Front (MTF)

Una codifica che, dato un alfabeto ordinato, rimpiazza i simboli con un vettore di interi che rappresentano l'index $X$ dei "simboli usati recentemente".
- Inizializza $X$ con l'alfabeto ordinato
- Per ogni simbolo $s$ del testo:
	- Codificalo nella posizione dove $s$ compare in $X$
	- In $X$, sposta $s$ in prima posizione

Dopo la codifica, i numeri più piccoli sono i più probabili.

##### Codifica gamma

Se si vuole utilizzare la codifica MTF come compressione direttamente, si usa la codifica gamma.
Il suo scopo per codificare numeri positivi in un numero di bit non fisso (così che i numeri più piccoli richiedano meno bit per essere rappresentati).
È composto da:
- $\text{|n|-1}$ in codifica unaria
	- Una codifica unaria che rappresenta il numero $m$, inserisce $m-1$ *zeri* e $1$ *uno*
- I bit di $n$, eccetto il primo *uno*.

`[1, 010, 011, 00100, 00101, 00110, 00111, 0001000, 0001001, …]`

### LZ77

Algoritmo di compressione che costruisce il dizionario in modo che non ci sia bisogno di salvarlo: viene ricostruito durante la decompressione.
L'output della codifica consiste in una serie di triple:
- Un puntatore che indica quanto indietro guardare (di solito 12 bit)
	- I $2^n$ caratteri prima sono il dizionario
- La lunghezza della sottostringa (di solito 4 bit)
- Il carattere successivo

La codifica consiste nel cercare la sottostringa più lunga nel search buffer (che va da dove si è ora fino a dove il puntatore permette) che corrisponda alla sottostringa che c'è dopo. Il processo viene ripetuto finché non si raggiunge la fine del testo.
Nella tripla è possibile avere la lunghezza della sottostringa più grande del puntatore: ciò significa ripetere l'ultimo carattere.

Gzip è una variante dell'algoritmo.

#### LZ78

Il dizionario non è composto da caratteri, ma da frasi.
Invece che triplette, si usano coppie: indice della frase (presa completamente) e prossimo carattere. Questa nuova frase viene aggiunta al dizionario.
È impossibile avere più di una rappresentazione per una stringa.
Il dizionario può essere implementato con un albero.

Rispetto a LZ77, la decodifica è più lenta.
Inoltre, funziona male in situazioni a entropia molto bassa: non si comporta bene se c'è una lunga sequenza ripetuta tante volte (dato che nel dizionario la frase deve essere completa, potrebbe non riuscire a costruire quella sequenza come si deve).

### Run Length Encoding

Frequentemente utilizzato per le [[Informazione#^87a4de|sorgenti con memoria]].
- Codifica la sorgente usando un modello predittivo che "indovina" (0) o "sbaglia" (1)
- Con un buon predittore, si otterrà una sequenza con tantissimi 0 e pochi 1 (entropia bassa)
- Una sequenza di $n$ 0 e un 1 è detta *run di lunghezza $n$*
- Codifica questa sequenza in "tutte le lunghezze dei run" (località spaziale).
	- Con parole di codice composte da $k$ bit, è possibile rappresentare stringhe di lunghezza massima $2^k-1$
