# Storia informatica

Nata ad inizio 1900, riposta alla **crisi dei fondamenti**.

- Inizio 1600: sviluppo calcolo
    - Paradosso infinito
        - $\mathbb{N}=\mathbb{Z} (\equiv \mathbb{N}*\mathbb{N})$
    - Infinitesimi
        - $dx, dy \neq 0$
        - Chain rule: $\frac{dx}{dy}=\frac{dx}{dz}\frac{dz}{dy}$
    - Definizione limiti
    - …
- 1800 geometrie non-euclidee

La matematica sta perdendo il suo criterio di certezza.

## Crisi dei fondamenti

### Cantor, Dedekind

- Consistenza delle analisi <- Geometria
    - Teoria dei sistemi numerici
        - **Aritmetica** ($\mathbb{N},+,…$)

### Frege

- **Logismo**: fondare la matematica sulla logica (invece che il contrario)
- *Ideografia*
    - Libro che introduce tra le varie cose la **logica del primo ordine** (#FOL)
    - Modus ponens: $A \rightarrow B, A \vdash B$

Mancava solo di costruire l'aritmetica su questo linguaggio. Ma la teoria che creò è risultata inconsistente.

### Hilbert

Uno dei matematici più famosi del 1900, conosciuto per i lavori di logica e per i 23 problemi di Hilbert.

- La matematica si basava sul **metodo assiomatico**
    - Dagli assiomi si ottengono nuove formule, che diventano **teoremi**
    - #FOL (first-order logic) + Assiomi
        - Peano Arithmetic (PA)
            - $\forall{x} \quad \neg (0=Successor(x))$
            - $\forall x,y \quad x+y=y+x$
            - …
- Cosa deve avere una teoria T:
    - Consistenza
        - La teoria non contraddice se stessa $\neg(T \land \neg T)$
    - Completezza
        - La teoria dimostra tutto il dimostrabile $T \vdash A \lor T \vdash \neg A$)
    - Decidibilità
        - Data una formula nella FOL, esiste una procedura meccanica che determina se la formula è dimostrabile.

Il lavoro di un matematico è dimostrare i teoremi, quindi una procedura che consente ciò li toglierebbe il lavoro.

Gödel dimostra che la FOL è completa. Anche l'aritmetica di Peano lo è? Gödel dimostra il **teorema di incompletezza**: la logica dell'aritmetica di Peano (e qualsiasi sistema logico che codifica l'aritmetica) non è completa, o se è completa è inconsistente.

Resta però la decidibilità.

FOL: $FOL \vdash A$

### Paradosso di Russel

$R=\{x|x \not \in x\}$

$R \in R \iff R \not \in R$

### Church (1930)

Funzioni ricorsive $\equiv$ [[λ-calcolo]] $\equiv$ [[Macchina di Turing]]

Vecchia definizione funzione: $\{(x,y)|f(x)=y\}$

Church: definizione di funzione come regola. **Astrazione**.

#### Tesi di Church-Turing

> Se un problema è umanamente calcolabile, allora esisterà una [[macchina di Turing]] in grado di risolverlo (cioè di calcolarlo)
