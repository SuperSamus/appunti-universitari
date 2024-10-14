## Codici a blocchi

In un codice a blocchi di dimensione $n$, ci sono $k$ bit sono utilizzati per il messaggio vero o proprio, e i restanti $n-k$ per ridondanza.
- Codici a ripetizione
- Codici a controllo di parità

Questi bit di ridondanza fanno sì che non tutte le parole di codice siano valide.
Questa fa sì che ci sia *distanza* tra le parole.
Data $d_{min}$ la distanza minima, e $t$ il numero di errori nella parola:
- È garantito che si può rilevare un errore se $t<d_{min}$
- È garantito che si può correggere un errore se $t<\frac{1}{2}d_{min}$

### Codice lineare

Ha le seguenti proprietà:
- Il vettore nullo è una parola valida
- La somma modulo 2 (per bit) di due parole è una parola valida
- Peso di Hamming: $w(X)=\text{Numero di bit uguali a 1 in }X$
- Distanza di Hamming: $d(X,Y)=w(X-Y)$
- $d_{min}=\min_\limits{X≠\overrightarrow{0}} w(X)$

#### Codice di Hamming

Codice lineare con le seguenti proprietà ($q=n-k$):
- $q≥3$
- $2^q≥n+1$
In questo modo, $d_{min}≥3$

### Codice sistematico

Nel blocco, i $k$ bit del messaggio vengono tutti prima dei $n-k$ bit di ridondanza: $X=(M|C)$

Si può rappresentare la generazione di $X$ con una *matrice generatrice*: $X=MG$, dove $G=[I_k,P]$.

>[!info]
>Per il codice di Hamming, è necessario e sufficient che ogni riga di $G$, e ogni combinazione lineare di ogni riga di $g$, abbia almeno 3 bit $1$.

Per la decodifica, si utilizza una matrice di controllo di parità $H=[P^T,I_q]$.

Chiamando $Y$ la parola $X$ passata per il canale rumoroso, si ha la *sindrome* $S=YH^T$, di dimensione $q$. Se $S$ è un vettore nullo, allora $Y$ è una parola valida, altrimenti non lo è.

- $Y=X+E$
- $S=EH^T$

Per la correzione, dato che $|S|<|E|$, ci sono diversi possibili vettori di errore associati alla sindrome. Si cerca quindi il vettore di errore più probabile (quello che ha peso minore).

### Codice ciclico

Codice lineare, con la proprietà che per ogni parola valida, la parola "ruotata" è anch'essa valida.

Rappresentando le parole come polinomi, con coefficienti modulo 2, si ha:
$X(p)=x_{n-1}p^{n-1}+x_{n-2}p^{n-2}+…+x_1p+x_0$

Sono basati sui *campi di Galois*: quindi, le operazioni di addizione, sottrazione, moltiplicazione e divisione tra membri del campo avranno come risultato un membro del campo.

Se $X'$ è $X$ ruotato a sinistra di 1, l'equivalente è:
- $pX(p)+X'(p)=x_{n-1}p^n+x_{n-1}=x_{n-1}(p^n+1)$
- $X'(p)=x_{n-1}(p^n+1)+pX(p)=pX(p)\mod (p^n+1)$

Caso generico, con $X$ ruotato di $i$:
$X^{(i)}(p)=Q(p)(p^n+1)+p^iX(p)=p^iX(p)\mod (p^n+1)$
Dove $Q(p)$ è un polinomio di grado non superiore a $i-1$.

##### Generazione

Anche il blocco che rappresenta il messaggio e il generatore si possono rappresentare come polinomi $Q_M(p)$ (di grado $k$) e $G(p)$ (di grado $q$) rispettivamente.
$X(p)=Q_M(p)G(p)$

Un polinomio irriducibile (quindi di grado più basso possibile) $G(p)$ definisce completamente il campo, ed è sempre un fattore di $p^n+1$. Tutti i fattori di $p^n+1$ sono generatori.

L'equivalente matrice generatrice è (1° algoritmo, non sistematico):
$$G=\begin{bmatrix}g_0&g_1&…&g_q&0&0&…&0\\0&g_0&…&g_{q-1}&g_q&0&…&0\\⫶\\0&0&…&0&g_0&g_1&…&g_q\end{bmatrix}$$

Esempio generatore di Hamming $(7,4)$ è $X^3+X+1$

##### Parità

Dato $H(p)$ un polinomio tale che:
$H(p)=\frac{p^n+1}{G(p)}$
allora $H(p)$ è un *polinomio di controllo di parità*.

Dato che $X(p)$ è multiplo di $G(p)$, allora si ha:
$X(p)H(p)=0\mod (p^n+1)$

L'equivalente matrice di parità è (1° algoritmo, non sistematico):
$$H=\begin{bmatrix}h_k&h_{k-1}&…&h_0&0&0&…&0\\0&h_k&…&h_1&h_0&0&…&0\\⫶\\0&0&…&0&h_k&h_{k-1}&…&h_0\end{bmatrix}$$

##### Sindrome

Dato $Y(p)=X(p)+E(p)$, con $E(p)$ l'errore causato dal rumore, si ha la *sindrome*:
$S(p)=Y(p) \mod G(p)$

Data $e$ la capacità di correzione errori del codice, se $w(S(p))≤e$, allora $S(p)=E(p)$.

Nota che la dimensione della sindrome è di $n-k$, quindi i bit "coperti" dalla sindrome solo parziali (se il codice è sistematico, sono quelli di parità). Se gli errori sono da qualche altra parte, la condizione sopra non sarà soddisfatta. Il codice è ciclico: si può ruotare finché non si trova un codice che soddisfa la condizione sopra.

#### Codice ciclico sistematico

Il polinomio si può rappresentare come:
$X(p)=p^qM(p)+C(p)$

Dato che $X(p)=Q_M(p)G(p)$, allora:
- $\frac{p^qM(p)}{G(p)}=Q_M(p)+\frac{C(p)}{G(p)}$
- $C(p)=⌊p^qM(p)⌋ \mod G(p)$

Con questo, è possibile generare la matrice generatrice: basta fare questa operazione per tutti i messaggi da un bit ($I_k)$, e i vari resti sono le righe per $P$.

## Codice convoluzionale

Codice che ogni $k$ bit di input:
- Prende gli ultimi $kL$ bit di input ricevuti
- Il generatore è una serie di $n<k$ somme di modulo 2: ciascuna, prende specifici ultimi $i$-esimi bit di input
- Restituisce $n$ bit di output

La codifica è facile, ma la decodifica non lo è. Questo tipo di codice è una buona idea, se l'input viene generato da un dispositivo poco potente, ma decodificato da un dispositivo potente.

Per via della memoria di dimensione $L$, si può rappresentare questo sistema come una macchina di stati (con $2^{L-1}$ stati), le cui transizioni si possono a loro volta rappresentare come un traliccio.

- Distanza per la colonna $i$: si considera $i=0$ la colonna di un percorso il cui output è solo 0. Il risultato equivale al peso minimo del percorso fino alla colonna $i$.
	- La funzione è non decrescente all'aumentare di $i$.
- Distanza minima: distanza con $i=L$.
- Distanza libera: distanza per $i→∞$, o il peso minimo del percorso che torna nello stato iniziale.

#### Algoritmo di Viterbi

Algoritmo di decodifica che, ricevuto un messaggio modificato dal rumore, cerca il percorso con la distanza minima.
Il miglior algoritmo in termini di accuratezza, ma il peggiore in termini di performance: il numero di percorsi equivale a $2^L$, quindi il tempo necessario per la decodifica cresce esponenzialmente all'aumentare di $L$.

Dato che certi percorsi si ricongiungono, è possibile tagliare via quelli meno probabili.
Per risparmiare memoria, i passaggi "vecchi" si possono decodificare quando, dopo un certo numero di passaggi (di solito 5), è difficile che i vecchi percorsi alternativi serviranno a qualcosa.

#### Decodifica sequenziale

Per ogni passo, viene scelto il percorso con la metrica migliore. Si però il percorso si rivela troppo improbabile, viene fatto backtracking.

Il valore atteso della metrica al nodo $i-esimo$ è $ikP_{be}$. Se viene superata la soglia $ikP_{be}+Δ$, viene eseguito il backtracking.

- $Δ$ troppo alto: rischio di tenere un percorso sbagliato
- $Δ$ troppo basso: il backtracking viene fatto così frequentemente, che si perde più tempo rispetto all'algoritmo di Viterbi.

#### Decodifica a retroazione

Implementazione a livello hardware. Molto veloce, ma grande rischio di errori.

## Strategie ARQ e FEC

Utilizzate nel caso gli errori sono un misto tra errori indipendenti e errori burst.
