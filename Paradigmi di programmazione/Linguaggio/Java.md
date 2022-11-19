# Java

Linguaggio di programmazione nato negli anni '90 da Sun Microsystems.

Obiettivi:
- Semplificare la programmazione rispetto a C/C++ (es. garbage collection)
- Indipendenza dalla piattaforma (il codice è compilato in bytecode ed eseguito dalla Java Virtual Machine (JVM))
- Modularizzabilità (è fortemente [[Programmazione orientata agli oggetti|orientato agli oggetti]])
- Robustezzza e sicurezza con controlli sia statici (compilatore) che dinamici (JVM)

Un programma Java è un insieme di classi, di cui una avrà il metodo `main` (che deve essere per forza `static`). I metodi `static` si possono chiamare senza istanziare la classe.

I membri di una classe si possono definire `public` (tutti ci possono accedere) o `private` (solo la classe stessa ci può accedere) in modo da fare *information hiding* (serviranno dei *getter* o *setter* pubblici per accederci, che sicuramente limiteranno cosa ci si può fare dall'esterno).

Non ci sono *puntatori*, ma ci sono *riferimenti* a oggetti.

## Interfacce

Le interfacce contengono una specifica astratta della classe ([[Programmazione orientata agli oggetti#^63e8cc|ADT]]). La relazione è creata esplicitamente con `implements` ([[Programmazione orientata agli oggetti#^83e369|nominal subtyping]]). È possibile implementare più interfacce, anche se potrebbe creare il problema del diamante.

È possibile dichiarare le variabili che hanno un supertipo come tipo, e assegnarle un oggetto di tipo sottotipo. Ciò creerà un divario: il *tipo apparente* (il supertipo) e il *tipo effettivo* (il sottotipo, che influenza quale funzione venga effettivamente chiamata (dynamic dispatch)).

Quest'ultimo potrebbe non essere noto a tempo di compilazione, ma si può testare il tipo effettivo e provare a forzarlo in runtime con un *type cast*.  Il type cast è implicito da un sottotipo e supertipo (upcast), ma deve essere esplicito da un supertipo a un sottotipo (downcast), e può fallire.
