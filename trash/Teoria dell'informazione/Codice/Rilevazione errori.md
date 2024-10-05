### Codici a blocchi

In un codice a blocchi di dimensione $n$, ci sono $k$ bit sono utilizzati per il messaggio vero o proprio, e i restanti $n-k$ per ridondanza.
- Codici a ripetizione
- Codici a controllo di parità

Questi bit di ridondanza fanno sì che non tutte le parole di codice siano valide.
Questa fa sì che ci sia *distanza* tra le parole.
Data $d_{min}$ la distanza minima, e $t$ il numero di errori nella parola:
- È garantito che si può rilevare un errore se $t<d_{min}$
- È garantito che si può correggere un errore se $t<\frac{1}{2}d_{min}$

#### Codice lineare

Ha le seguenti proprietà:
- Il vettore nullo è una parola valida
- La somma modulo 2 (per bit) di due parole è una parola valida

Peso: $w(X)=\text{Numero di bit uguali a 1}$
$d_{min}=\min_X w(X)$

##### Codice di Hamming

Codice lineare con le seguenti proprietà ($q=n-k$):
- $q≥3$
- $n=2^{q-1}$

#### Codice sistematico

Nel blocco, i $k$ bit del messaggio vengono tutti prima dei $n-k$  bit di ridondanza: $X=(M|C)$

Si può rappresentare la generazione di $X$ con una *matrice generatrice*: $X=MG$, dove $G=[I_k,P]$.

Per la decodifica, si utilizza una matrice di controllo di parità $H=[P^T,I_q]$.

Chiamando $Y$ la parola $X$ passata per il canale rumoroso, si ha la *sindrome* $S=YH^T$, di dimensione $q$. Se $S$ è un vettore nullo, allora $Y$ è una parola valida, altrimenti, non lo è.

- $Y=X+E$
- $S=EH^T$

Per la correzione, dato che $|S|<|E|$, ci sono diversi possibili vettori di errore associati alla sindrome. Si cerca quindi il vettore di errore più probabile (di solito, quello che ha peso minore).

#### Codice ciclico

Codice lineare, con la proprietà che per ogni parola valida $X$, la parola "ruotata" $X'$ è anch'essa valida.

Rappresentando le parole come polinomi, con coefficienti modulo 2, si ha:
$X(p)=x_{n-1}p^{n-1}+x_{n-2}p^{n-2}+...+x_1p+x_0$

Dato $X'$ una rotazione a sinistra di 1, si ha:
$pX(p)+X'(p)=x_{n-1}p^n+x_n{n-1}=x_{n-1}(p^n+1)$
Che per linearità, è valido.

Anche il blocco che rappresenta il messaggio e il generatore si possono rappresentare come polinomi $Q_M(p)$ (di grado $k$) e $G(p)$ (di grado $q$).
$X(p)=Q_M(p)G(p)$

È quindi necessario che $G(P)$ sia un fattore di $p^n+1$. Non per forza vuol dire che produrrà un buon codice.

##### Codice ciclico sistematico

Il polinomio si può rappresentare come:
$X(p)=p^qM(p)+C(p)$

Dato che $X(p)=Q_M(p)G(p)$, allora:
- $\frac{p^qM(p)}{G(p)}=Q_M(p)+\frac{C(p)}{G(p)}$
- $C(p)=⌊p^qM(p)⌋ \mod G(p)$

Infine, la sindrome:
$S(p)=Y(p) \mod G(p)$
