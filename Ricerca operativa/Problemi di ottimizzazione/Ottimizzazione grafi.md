# Grafi

In un [[Problemi di ottimizzazione|problema di ottimizzazione]] di un grafo $G=(N,A)$, con archi $(i,j)∈A$, di solito si hanno questi dati:
- $x_{ij}$ flusso nell'arco $(i,j)$
- $b_i$ come il bilancio del nodo $i$
	- $b_i$ può essere positivo o negativo per scegliere a piacere tra *pozzo* o *sorgente*

Generalmente si ha questo vincolo:
- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = b_i \quad i ∈ N$
	- Stella entrante: $BN(i)=\{j ∈ N : (j,i) ∈ A\}$
	- Stella uscente: $FN(i)=\{j ∈ N : (i,j) ∈ A\}$

## Cammino minimo

Abbiamo una sorgente $s∈N$ e una destinazione $t∈N$ a cui dobbiamo trasmettere un singolo elemento, gli archi che hanno un costo $c_{ij}$.

Da qui si può rappresentare un problema di cammino minimo con:

Vincoli:
- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = \begin{cases} -1 &\text{se } i=s \\ 1 &\text{se } i=t \\ 0 &\text{altrimenti} \end{cases} \quad i ∈ N$

Da trovare:
- $x_{ij}=\begin{cases} 1 &\text{se si passa per l'arco } (i,j)∈A \\ 0 &\text{altrimenti} \end{cases}$

Funzione obiettivo min: $∑\limits_{(i,j)∈A}x_{ij}c_{ij}$

### Problema non intero

Questi vincoli lo rendono un problema di programmazione lineare intera: i vincoli di interezza (di $x_{ij}$ in questo caso) rendono il calcolo della soluzione più complicato. Si può fare invece con $0≤x_{ij}≤1$?

Per esempio, immaginiamo che in questo grafo questa sia la soluzione ottima:
```mermaid
flowchart LR
s -- 1/2 --> A & B
A -- 1/2 --> C
s --> C
B -- 1/2 --> C
C -- 1/2 --> D & E
D -- 1/2 --> t
C --> t
E -- 1/2 --> t
```

Non è un cammino. Però:
- I bilanci nel vincolo di conservazione sono soddisfatti
- Assumiamo che con il vincolo di interezza la soluzione ottima sia $s→C→t$, e che sia peggiore.
	- Ciò dovrebbe voler dire che il costo di ½ cammino sopra + ½ cammino sotto < cammino centrale.
	- Inoltre, i cammini sopra e sotto dovrebbero costare uguali, sennò sarebbe meglio prendere interamente uno dei due.
		- Ma a questo punto si può anche prendere interamente uno dei due cammini e non cambierebbe il costo.

Quindi, rimuovere il vincolo di interezza non cambia il costo totale. I cammini con $x_{ij}$ frazionario sono semplicemente strade alternative.

#### Distribuendo a tutti

La radice $s$ deve trasmettere un pacchetto a tutti i nodi. Gli archi inoltre vanno comprati ogni volta che ci si passa.

Vincoli:
- Conservazione del flusso: $∑\limits_{j∈BN(i)} x_{ji} - ∑\limits_{j∈FN(i)} x_{ij} = b_i \quad i ∈ N$
	- $b_i=\begin{cases} -(|N|-1) &\text{se } i=s \\ 1 &\text{altrimenti} \end{cases}$

$x_{ij}$ sarà il numero di cammini che usano l'arco $(i,j)$, quindi $x_{ij} ∉ \{0,1\}$, bensì $x≥0$.

Nota che è possibile che il grafo non sia connesso, in questo caso non esisterà soluzione. Si può risolvere creando un arco esageratamente costoso (se $+∞$ non si potesse fare, $(|N|-1)(\max\limits_{(i,j)∈A} c_{ij})+1$ va bene) dalla radice a tutti i nodi.

Stiamo anche assumendo che non ci siano cicli di costo negativo.

### Albero dei cammini minimi

Questo percorso non è di cammino minimo:

```mermaid
flowchart LR
A --> B
s --> A & B
B --> C & D
```

Però uno di questi due potrebbe esserlo:

Se s→A→B è meglio rispetto a s→B:

```mermaid
flowchart LR
A --> B
s --> A
B --> C & D
```


Se s→B è meglio rispetto a s→A→B:

```mermaid
flowchart LR
s --> A & B
B --> C & D
```

---

Prendiamo questo grafo, dove le linee non tratteggiate sono di commini minimi:

```mermaid
flowchart LR
r --> A
r --> C --> i
A --> B
B --> h
h --> j
A .-> h
r .-> B .-> j
C .-> B
i .-> j .-> C
```

$d_h \; d_j \; d_i$ Costo dei cammini da $r$ sull'albero

$d_h+c_{hj}=d_j$

$d_i+c_{ij}≥d_j$

Quindi:
- Condizioni di Bellman
	- $(N,A_T)$ è un albero dei cammini minimi ⇔ $d_i+c_{ij}≥d_j \quad ∀(i,j)∈A$
- Etichetta del nodo $i$
	- $d_i=$ costo dell'unico cammino da $r$ a $i$ sull'albero ($d_r=0$)

#### Verifica

Questo albero è dei cammini minimi?

```mermaid
flowchart LR
1 -- 5 --> 2
2 -- 5 --> 4
1 -- 7 --> 3
2 -. 1 .-> 3
3 -. 3 .-> 4
2 -- 3 --> 5
3 -. 2 .-> 5
5 -. 1 .-> 4
```

- $d_1=0$
- $d_2=5$
- $d_3=7$
- $d_4=10$
- $d_5=8$

Dobbiamo verificare la condizione di Bellman per ogni arco che non è dell'albero.
- $d_2+c_{23}=5+1=6<7=d_3$

E abbiamo già verificato che la condizione di Bellman non è verificata: l'albero non è dei cammini minimi.

Per certificare che non lo è basta solo trovare una condizione falsa. Non tutte le etichette sbagliate hanno per forza la condizione falsa, per esempio:
$d_4=d_2+c_{24}=5+5=10=d_3+c_{34}=7+3=10$ (avevamo visto che dovrebbe essere $d_3=6$, e $6+3=9<10=d_4$, ma dato che controlliamo con il $d_3$ sbagliato non si noterebbe che anche $d_4$ è sbagliato)

per certificare è di cammino minimo bisogna controllare tutti.
