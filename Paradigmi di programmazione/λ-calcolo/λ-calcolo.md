# λ-calcolo

Sono un linguaggio generale per descrivere funzione e operatori come si combinano tra di loro. È di *ordine superiore*: può avere funzioni come input e output. Arricchibile.

## Esempio in matematica

$x-y$, è ambigua da sola:

- Espressione statica, quantità nelle incognite $x$ e $y$
- Funzione in $x$: $f(x)=x-y$
- Funzione in y: $g(y)=x-y$
- Funzione in $x$ e $y$: $h(x,y)=x-y$

Una notazione deve essere *sistematica*, e $x-y$ da solo non lo è.

## Notazione di Church

Le funzioni sopra diventano rispettivamente:

- $f$: $λx.x-y$
- $g$: $λy.x-y$
- $h$: $λx.λy.x-y$

Per usare le funzioni si fa per esempio $(λx.x-y)(1)$

Ciò permette di avere funzioni in output: $(λx.λy.x-y)(a)(b)=(λy.a-y)(b)=a-b$

$xy$ vuol dire applicare $y$ a $x$ (sintatticamente, in matematica sarebbe una moltiplicazione).

### Esempio

```javascript
function p(x) {
    return x*x+3*x+6;
}
p(5);
```

$$
p(x)=x^2+3x+6=(λx.x^2+3x+6) \\
p(5)=5^2+3*5+6=(λx.x^2+3x+6)5
$$

### *Curry*ing

$A ⨉ B → C ≡ A → (B → C)$

Il currying è il seguente isomorfismo, che trasforma una funzione in una da ordine superiore: $λx,y.t → λx.λy.t$

### Esempio

Funzione che prende in input:

- Una funzione
- Un argomento

E restituisce la funzione applicata 2 volte all'argomento.

$λy.λx.y(y(x))$

Se gli diamo un argomento $λz.z+z$ (ovvero si fa ($λy.λx.y(y(x))(λz.z+z)$) otteniamo la nuova funzione $λx.x+x+x+x$.

## Definizione λ-termini

$t,s::=x|(λx.t)|(ts)$
variabile|λ-astrazione|astrazione

### Esempi

- $(λx.x)$ è un termine, rappresenta la generica applicazione di *identità* ($I$). Non si può fare in matematica: $f(x)=x$ ha un dominio e codominio, non può essere generico su tutti i domini.
- $(λx.y)$ restituisce la costante y.
- $(λz.y)$ fa la stessa cosa, ma è considerata un'applicazione diversa.
- $x ∈ λ$
- $t ∈ λ⇒(λx.t) ∈ λ$
- $t ∈ λ\; \text{se} \; λ⇒(ts) ∈ λ$
- $((λy.y)(λx.(xy)))$
- $(x(λx.(λx.x)))$
- $(x(λy.(λz.z)))$

## Convenzione notazionale

- $(λx.t) \; \text{quando sta da solo}=λx.t$
- $((((ts_1)s_2)…)s_n)=ts_1s_2…s_n$
- $(λx.(ts))=λx.ts$
- $(λx.λy.λz.xyz)=(λxyz.xyz)$

## Precisazioni

- $t → \text{procedura/operatore}$
- $(ts) → \text{risultato dell'applicazione t ad s}$
- $(λx.t)s → \text{la funzione il cui valore in s viene calcolcato sostituendo s ad x in t}$

$(λx.3x^2+4x+6)s=3s^2+4s+6$

$(λx.t)s → t[s/x]$ ([[Sostituzione]])

$(λx.xy)x$: x è un segnaposto solo dentro la parentesi, fuori è solo una variabile, perché non è più legata dal lambda. $x ∈ FV(t)$

## Variabili libere (FV)

- $FV(x)=\{x\}$
- $FV(ts)=FV(t) ∪ FV(s)$
- $FV(λx.t)=FV(t) \\ \{x\}$

$t$ è *chiuso* se $FV(t)=∅$
