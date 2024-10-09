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
- $n=2^{q-1}$

### Codice sistematico

Nel blocco, i $k$ bit del messaggio vengono tutti prima dei $n-k$ bit di ridondanza: $X=(M|C)$

Si può rappresentare la generazione di $X$ con una *matrice generatrice*: $X=MG$, dove $G=[I_k,P]$.

Per la decodifica, si utilizza una matrice di controllo di parità $H=[P^T,I_q]$.

Chiamando $Y$ la parola $X$ passata per il canale rumoroso, si ha la *sindrome* $S=YH^T$, di dimensione $q$. Se $S$ è un vettore nullo, allora $Y$ è una parola valida, altrimenti non lo è.

- $Y=X+E$
- $S=EH^T$

Per la correzione, dato che $|S|<|E|$, ci sono diversi possibili vettori di errore associati alla sindrome. Si cerca quindi il vettore di errore più probabile (di solito, quello che ha peso minore).

### Codice ciclico

Codice lineare, con la proprietà che per ogni parola valida, la parola "ruotata" è anch'essa valida.

Rappresentando le parole come polinomi, con coefficienti modulo 2, si ha:
$X(p)=x_{n-1}p^{n-1}+x_{n-2}p^{n-2}+…+x_1p+x_0$

Sono basati sui *campi di Galois*: quindi, le operazioni di addizione, sottrazione, moltiplicazione e divisione tra membri del campo avranno come risultato un membro del campo.

Se $X'$ è $X$ ruotato a sinistra di 1, l'equivalente è:
- $pX(p)+X'(p)=x_{n-1}p^n+x_{n-1}=x_{n-1}(p^n+1)$
- $X'(p)=x_{n-1}(p^n+1)+pX(p)$
Cioè il resto della divisione tra $pX(p)$ e $p^n+1$.

Caso generico, con $X$ ruotato di $i$:
$X^{(i)}(p)=Q(p)(p^n+1)+p^iX(p)$
Dove $Q(p)$ è un polinomio di grado non superiore a $i-1$.

##### Generazione

Anche il blocco che rappresenta il messaggio e il generatore si possono rappresentare come polinomi $Q_M(p)$ (di grado $k$) e $G(p)$ (di grado $q$) rispettivamente.
$X(p)=Q_M(p)G(p)$

$G(p)$ definisce completamente il campo, ed è sempre un fattore di $p^n+1$. Tutti i fattori di $p^n+1$ sono generatori, e sono irriducibili.

Dato $H(p)$ un polinomio tale che:
$G(p)H(p)=0\mod (p^n+1)$
allora $H(p)$ è un *polinomio di controllo di parità*.

Dato che $X(p)$ è multiplo di $G(p)$, allora si ha anche:
$X(p)H(p)=0\mod (p^n+1)$

##### Errore

Dato $Y(p)=X(p)+E(p)$, con $E(p)$ l'errore causato dal rumore, si ha la *sindrome*:
$S(p)=Y(p) \mod G(p)$

La dimensione della sindrome è di $n-k$, quindi gli errori sono solo quelli nei bit di parità, ma... il codice è ciclico.

Data $e$ la capacità di correzione errori del codice, se $w(S(p))≤e$, allora $S(p)=E(p)$.

La limitazione del fatto che gli errori devono avvenire sui bit di parità si può aggirare perché... il codice è ciclico.

#### Codice ciclico sistematico

Il polinomio si può rappresentare come:
$X(p)=p^qM(p)+C(p)$

Dato che $X(p)=Q_M(p)G(p)$, allora:
- $\frac{p^qM(p)}{G(p)}=Q_M(p)+\frac{C(p)}{G(p)}$
- $C(p)=⌊p^qM(p)⌋ \mod G(p)$


