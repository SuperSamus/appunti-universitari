# Java

Linguaggio di programmazione nato negli anni '90 da Sun Microsystems.

Obiettivi:
- Semplificare la programmazione rispetto a C/C++ (es. garbage collection)
- Indipendenza dalla piattaforma (il codice è compilato in bytecode ed eseguito dalla Java Virtual Machine (JVM))
- Modularizzabilità (è fortemente [[Programmazione orientata agli oggetti|orientato agli oggetti]])
- Robustezzza e sicurezza con controlli sia statici (compilatore) che dinamici (JVM)

Un programma Java è un insieme di classi, di cui una avrà il metodo `main` (che deve essere per forza `static`). I metodi `static` si possono chiamare senza istanziare la classe.

I membri di una classe si possono definire `public` (tutti ci possono accedere) o `private` (solo la classe stessa ci può accedere) in modo da fare *information hiding* (serviranno dei *getter* o *setter* pubblici per accederci, che sicuramente limiteranno cosa ci si può fare dall'esterno).

Ci sono anche le *interfacce*, che contiene una specifica astratta della classe ([[Programmazione orientata agli oggetti#^63e8cc|ADT]]). La relazione è creata esplcitamente con `implements` ([[Programmazione orientata agli oggetti#^83e369|nominal subtyping]]).

Non ci sono *puntatori*, ma ci sono *riferimenti* a oggetti.