# λ-calculus

Sono un linguaggio generale per descrivere funzione e operatori come si combinano tra di loro. Arricchibile.

## Esempio in matematica

$x-y$, è ambigua da sola:

- Espressione statica, quantità nelle incognite $x$ e $y$
- Funzione in $x$: $f(x)=x-y$
- Funzione in y: $g(y)=x-y$
- Funzione in $x$ e $y$: $h(x,y)=x-y$

Una notazione deve essere *sistematica*, e $x-y$ da solo non lo è.

## Notazione di Church

Le funzioni sopra diventano rispettivamente:

- $f$: $\lambda x.x-y$
- $g$: $\lambda y.x-y$
- $h$: $\lambda x. \lambda y.x-y$

Per usare le funzioni si fa per esempio $(\lambda x.x-y)(1)$

Ciò permette di avere funzioni in output: $(\lambda x. \lambda y.x-y)(a)(b)=(\lambda y.a-y)(b)=a-b$

$xy$ vuol dire applicare $y$ a $x$ (sintatticamente, in matematica sarebbe una moltiplicazione).

### *Curry*ing

$A \times B \rightarrow C \equiv A \rightarrow (B \rightarrow C)$

Il currying è il seguente isomorfismo, che trasforma una funzione in una da ordine superiore: $\lambda x,y.t \rightarrow \lambda x. \lambda y.t$

### Esempio

Funzione che prende in input:

- Una funzione
- Un argomento

E restituisce la funzione applicata 2 volte all'argomento.

$\lambda y. \lambda x. y(y(x))$

Se gli diamo un argomento $\lambda z.z+z$ (ovvero si fa ($\lambda y. \lambda x. y(y(x))(\lambda z.z+z)$) otteniamo la nuova funzione $\lambda x.x+x+x+x$.

## Definizione λ-termini

$t,s::=x|(\lambda x.t)|(ts)$
variabile|λ-astrazione|astrazione

### Esempi

- $(\lambda x.x)$ è un termine, rappresenta la generica applicazione di *identità*. Non si può fare in matematica: $f(x)=x$ ha un dominio e codominio, non può essere generico su tutti i domini.

- $(\lambda x.y)$ restituisce la costante y.

- $(\lambda z.y)$ fa la stessa cosa, ma è considerata un'applicazione diversa.

- $x \in \lambda$

- $t \in \lambda \Rightarrow (\lambda x.t) \in \lambda$

- $t \in \lambda \; \text{se} \; \lambda \Rightarrow (ts) \in \lambda$

- $((\lambda y.y)(\lambda x.(xy)))$

- $(x(\lambda x.(\lambda x.x)))$

- $(x(\lambda y. (\lambda z.z)))$


## Convenzione notazionale

- $(\lambda x.t) \; \text{quando sta da solo}=\lambda x.t$
- $((((ts_1)s_2)…)s_n)=ts_1s_2…s_n$
- $(\lambda x.(ts))=\lambda x.ts$
- $(\lambda x. \lambda y . \lambda z.xyz)=(\lambda xyz.xyz)$

## Precisazioni

- $t \rightarrow \text{procedura/operatore}$
- $(ts) \rightarrow \text{risultato dell'applicazione t ad s}$
- $(\lambda x.t)s \rightarrow \text{la funzione il cui valore in s viene calcolcato sostituendo s ad x in t}$

$(\lambda x.3x^2+4x+6)s=3s^2+4s+6$

$(\lambda x.t)s \rightarrow t[s/x]$ (sostituzione)

$(\lambda x.xy)x$: x è un segnaposto solo dentro la parentesi, fuori è solo una variabile, perché non è più legata dal lambda. $x \in FV(t)$

## Variabili libere (FV)

- $FV(x) =\{x\}$
- $FV(ts)=FV(t) \cup FV(s)$
- $FV(\lambda x.t)=FV(t) \setminus \{x\}$

### Esercizi

[[Esercizi λ-calcolo base]]