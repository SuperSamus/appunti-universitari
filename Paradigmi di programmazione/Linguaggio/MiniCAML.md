# MiniCAML

Il nostro subset di [[OCaml]], dove si implementerà anche un [[inteprete]].

$e::=\underline{n}|e+e|e*e|\underline{b}|ite(e,e,e)|\text{let }x=e \text{ in } e|λx.e|e \: e$

Variabili/identificatori:
- Costanti: $\underline{n},\underline{b}$
- Operazioni: $+,-,ite(\_,\_,\_)$
- Operazioni: $λx, \text{let } x =\_ \text{ in } \_$
- Tipi: $int \: bool$

```OCaml
type ide = string
type tname = TInt | TBool
type exp =
    | ExpInt of int
    | ExpBool of bool
    | Add of exp * exp
    | Let of ide * e * e
    | Lam of ide * e
    | App of exp * exp
```

$v::=\underline{n}|\underline{b}|λx.e$

## Ambiente

Le dichiarazioni `let` creano un ambiente. Per esempio:
```OCaml
let x = 3
x + x
```
$⤳x↦3|x+x$

La semantica operazionale non è una relazione da espressioni a valori, ma rispetto a un ambiente $Σ:ide→α$ (bisognerebbe aggiungere anche $option$).

$$
Σ🢒e⇒v
$$

Con $v::=\underline{n}|\underline{b}|〈x,e,Σ〉$

```OCaml
type a' env = ide -> a'
type val =
    | Int of int (* `ExpInt` è un `exp`, `Int` è un `val` *)
    | Bool of bool
    | Closure of ide * exp * val env
    | Unbound (* Se la variabile non c'è nell'ambiente *)
```

### Definizioni:
Rispetto all'altra descrizione formale di un [[linguaggio]], con queste semantica operazionale non è necessario descrivere la regole di [[sostituzione]].

#### Let
$$
\cfrac{Σ🢒e⇒v \quad Σ[x↦v]🢒e'⇒v'}{Σ🢒\text{let }x=e \text{ in } e'⇒v'}
$$

#### Chiusura
$$
\cfrac{}{Σ🢒λx.e⇒〈x,e,Σ〉}
$$
(Se venisse restituita la λ-espressione direttamente, si avrebbe uno *scoping dinamico* invece che *statico*)

#### Applicazione
$$
\cfrac{Σ🢒e⇒〈x,f,Δ〉 \quad Σ🢒e'⇒v \quad Δ[x↦v]🢒f⇒w}{Σ🢒e\:e'⇒w}
$$

#### "Esecuzione" variabile
$$
\cfrac{}{Σ🢒x⇒Σ(x)}
$$

## Bind

Lega una variabile all'ambiente: prende (tra le varie cose) un ambiente come input, per restituire un ambiente come output.

$bind:val\:env→ide→val→val\:env$

```OCaml
let bind s x v = fun y -> if (x = y) then v else (s y)
```

## Eval

$eval:exp→val\:env→val$

```OCaml
let rec eval e s = match e with
    | Add(e1,e2) ->
	    let v1 = eval e1 s
	    and v2 = eval e2 s
	    in int_plus v1 v2
	(*...*)

let intplus v1 v2 = match v1, v2 with
    | Int n1, Int n2 -> Int(n1+n2)
    (*...*)
```

$$
\cfrac{Σ🢒e_1⇒\underline{n_1} \quad Σ🢒e_1⇒\underline{n_2}}{Σ🢒Add(e_1,e_2)⇒\underline{n_1+n_2}}
$$
