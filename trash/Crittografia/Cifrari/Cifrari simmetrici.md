Funzione di cifratura: $c=C(m,k)$
Funzione di decifrazione: $m=D(c,k)$

### Cifrari simmetrici

Si basano sui *Principi di Shannon*:
- **Diffusione**: Il testo in chiaro si deve distribuire su tutto il crittogramma
	- Ogni carattere del crittogramma dipende da *tutti i caratteri* del blocco
- **Confusione**: Messaggio e chiave sono combinati tra loro in modo complesso, per rendere impossibile l'analisi statistica

#### DES (Data Encryption Standard)

Divide il messaggio in blocchi di 64 bit, ciascuno cifrato e decifrato indipendentemente dagli altri.
Queste operazioni vengono ripetute in $r$ fasi (round). Nel DES, $r=16$.
La chiave segreta $k$ è effettivamente di 56 bit: per ogni byte (8), i primi 7 bit sono scelti arbitrariamente, mentre l'ottavo è per il controllo di parità. Dalla chiave vengono create le sottochiavi per $r$.

Per ottenere le sottochiavi, si prende la chiave originaria e gli applica la permutazione CP-1 (che tra l'altro scarta tutti i multipli di 8): i primi 28 bit del risultato compongono $C[0]$, gli altri 28 bit compongono $D[0]$.
Per $i$ da $1$ a $16$:
- $C[i]=C[i-1]<<KS[i]$
- $D[i]=D[i-1]<<KS[i]$
	- KS è una tabella che indica di quanto ruotare a sinistra (1 o 2) per round
- $C[i]$ e $D[i]$ insieme subiscono una permutazione CP-2 che forma $k[i]$ (e scarta altri 8 bit, lasciandone 48).

Per il messaggio, i bit del blocco subiscono una permutazione iniziale IP: i primi 32 bit del risultato compongono $L[0]$, gli altri 32 bit compongono $R[0]$.
Per $i$ da $1$ a $16$, si applica il *Feistel network*:
- $L[i]=R[i-1]$
- $R[i]=L[i-1]⊕f(R[i-1],k[i])$
	- $⊕$ è l'operazione XOR
	- $f$ è una funzione non lineare

$R[16]$ e $L[16]$ insieme subiscono una permutazione finale FP (che è l'inverso di IP). Il risultato è il crittogramma del blocco.

>[!note]
>Le permutazioni IP e FP non hanno un ruolo crittografico, ma solo di performance.

La funzione $f$:
- $D[i-1]$ viene espanso da 32 bit a 48 bit, usando la tabella di selezione bit E
	- Quello che E fa: dividi $D[i-1]$ in 8 blocchi da 4 bit: $b_i,b_{i+1},b_{i+2},b_{i+3}$.
	  Per ogni blocco, l'output $E(D[i-1])$ è un altro blocco da 6 bit: $b_{i-1},b_i,b_{i+1},b_{i+2},b_{i+3},b_{i+4}$ (ovviamente, $i$ subisce avvolgimento aritmetico a 32)
- Esegue $E(D[i-1])⊕k[i]$
- Usa le *S-box* per applicare la sostituzione, e per portare l'output da 48 bit a 32 bit
	- Dividi l'input in 8 blocchi $B_i$ da 6 bit: per $i$ da 1 a 8, applica $S_i(B_i)$, ciascuno con un output da 4 bit
		- Ogni tabella $S_i$ ha 4 righe e 16 colonne. Con l'input di 6 bit, il primo e l'ultimo bit determinano la riga, e i 4 bit in mezzo determinano la colonna.
- Finalmente, combina gli output delle S-box e applica la permutazione $P$
	- Questo affinché le S-box non lavorino sempre con gli stessi input

>[!info]
>#### S-box
>
>Componente base dei cifrari simmetrici per effettuare la sostituzione, allo scopo di assicurare la proprietà di confusione.
>È una tabella (che nei cifrari più complessi dipende da una chiave, ma nel DES sono 8 tabelle fisse) che trasforma un input di dimensione $m$ in un output di dimensione $n$.

>[!note]
>Se $C_{DES}(m,k)=c$, allora $C_{DES}(\bar{m},\bar{k})=\bar{c}$.
>Infatti:
>- Tutte le sottochiavi sono ottenute con permutazioni e spostamenti, quindi se per ogni $i$ le sottochiavi di $k$ sono $k[i]$, allora per $\bar{k}$ sono $\overline{k[i]}$
>- $f(R[i-1],k[i])=f(\overline{R[i-1]},\overline{k[i]})$

Per attaccare il DES, c'è bisogno di usare attacchi di forza bruta: esistono altri tipi di attacchi, ma sono praticabili solo in teoria.
Tuttavia, una chiave di 56 bit è considerata corta al giorno d'oggi.

##### Triple DES

Date due chiavi arbitrarie $k_1$ e $k_2$, allora per tutte le chiavi $k_3$:
$$C_{DES}(C_{DES}(m, k_1), k_2)≠C_{DES}(m, k_3)$$

Questo significherebbe che applicare due volte il DES con due chiavi, equivarrebbe ad avere una chiave da 112 bit.
Problema: *meet-in-the-middle attack*, se l'attaccante conosce una qualsiasi coppia arbitraria $<m,c>$:
- Per ogni $k_1$, calcola a salva $C_{DES}(m, k_1)$ in una tabella
- Per ogni $k_2$ calcola $D_{DES}(c, k_2)$ e cercalo nella tabella
Quindi, la complessità diventa cercare due chiavi da 56 bit (che è come cercarne una da 57 bit).

Soluzione: usa tre chiavi:
$$C_{DES}(D_{DES}(C_{DES}(m, k_1)), k_2),k_3)≠C_{DES}(m, k_3)$$

Ora con il meet-in-the-middle attack, il costo è come cercare una chiave da 112 bit.

#### AES (Advanced Encryption Standard)

Cifrario simmetrico, con chiavi di 128 bit o 256 bit.
Divide il messaggio in blocchi lunghi quanto la chiave, e la chiave viene applicata indipendentemente per blocco.
TODO

### Cipher Block Chaining (CBC)

Avere la cifratura applicata per blocco costituisce dei problemi:
- La diffusione è limitata al blocco
- Se due blocchi sono uguali, anche la loro cifratura sarà la stessa
- La periodicità del crittogramma rende la crittoanalisi più facile

Soluzione: prima di cifrare un blocco, applica lo XOR della cifratura del blocco precedente.
Ciò renderà la cifratura più lenta (in quanto i blocchi non possono più essere cifrati in parallelo, ma dovranno essere cifrati sequenzialmente), ma la decifrazione resterà parallela.
