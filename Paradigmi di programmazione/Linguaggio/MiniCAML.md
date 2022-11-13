# MiniCAML

Il nostro subset di [[OCaml]], dove si implementerà anche un [[inteprete]].

(Nota: il professore non riesce ad essere coerente con la sintassi)

$e::=\underline{n}|\underline{b}|e+e|e*e|ite(e,e,e)|λx.e|e \: e|\text{let }x=e \text{ in } e|\text{let rec }f\:x=e\text{ in }e$

Variabili/identificatori:
- Costanti: $\underline{n},\underline{b}$
- Operazioni: $+,-,ite(\_,\_,\_)$
- Operazioni: $λx, \text{let } x =\_ \text{ in } \_$
- Tipi: $int \: bool$

```OCaml
type ide = string
type exp =
    | ExpInt of int
    | ExpBool of bool
    | Add of exp * exp
    | Let of ide * exp * exp
    | LetRec of ide * ide * exp * exp
    | Lam of ide * exp
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

Con $v::=\underline{n}|\underline{b}|〈x,e,Σ〉|〈f,x,e,Σ〉$

```OCaml
type a' env = ide -> a'
type val =
    | Int of int (* `ExpInt` è un `exp`, `Int` è un `val` *)
    | Bool of bool
    | Closure of ide * exp * val env
    | ClosureRec of ide * ide * exp * val env
    | Unbound (* Se la variabile non c'è nell'ambiente *)
```

### Bind

Lega una variabile all'ambiente: prende (tra le varie cose) un ambiente come input, per restituire un ambiente come output.

$bind:val\:env→ide→val→val\:env$

```OCaml
let bind s x v = fun y -> if (x = y) then v else (s y)
```

### Definizioni
Rispetto all'altra descrizione formale di un [[linguaggio]], con queste semantica operazionale non è necessario descrivere la regole di [[sostituzione]].

#### Somma
$$
\cfrac{Σ🢒e_1⇒\underline{n_1} \quad Σ🢒e_1⇒\underline{n_2}}{Σ🢒Add(e_1,e_2)⇒\underline{n_1+n_2}}
$$

#### Let
$$
\cfrac{Σ🢒e⇒v \quad Σ[x↦v]🢒e'⇒v'}{Σ🢒\text{let }x=e \text{ in } e'⇒v'}
$$

#### LetRec
(Credo, perché il professore ha scritto qualcosa di insensato)
$$
\cfrac{Σ🢒e⇒v \quad Σ[f↦〈f,x,e',Σ〉][e↦v]🢒e'⇒v'}{Σ🢒\text{let rec }f\:x=e \text{ in } e'⇒v'}
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

## Eval

$eval:exp→val\:env→val$

```OCaml
let intplus v1 v2 = match v1, v2 with
    | Int n1, Int n2 -> Int(n1+n2)
    (*...*)

let rec eval e s = match e with
    | Add(e1,e2) ->
	    let v1 = eval e1 s
	    and v2 = eval e2 s
	    in int_plus v1 v2
	| Let(x,e1,e2) ->
	    let v = eval e1 s
	    in eval e2 (bind s x v)
	| 
	| Lam(x,e) -> Closure(x,e,s)
	| App(e1,e2) ->
	    let clos = eval e1 s
	    and v = eval e2 s
	    in match clos with
	        | Closure(x,f,p) -> eval f (bind p x v)
	        | _ -> error
	(*...*)
```
