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

Con $v::=\underline{n}|\underline{b}|〈x,e,Σ〉|〈f,x,t,Φ〉$

```OCaml
type a' env = ide -> a'
type val =
    | Int of int (* `ExpInt` è un `exp`, `Int` è un `val` *)
    | Bool of bool
    | Closure of ide * exp * val env
    | ClosureRec of ide * ide * exp * exp (* Invece che contenere un ambiente con le variabili fuori, viene contenuta la funzione che deve essere chiamata ricorsivamente *)
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

##### LetRec
$$
\cfrac{Σ[f↦〈f,x,e,e'〉]🢒e'⇒v'}{Σ🢒\text{let rec }f\:x=e \text{ in } e'⇒v'}
$$

#### Chiusura
$$
\cfrac{}{Σ🢒λx.e⇒〈x,e,Σ〉}
$$
(Se venisse restituita la λ-espressione direttamente, si avrebbe uno *scoping dinamico* invece che *statico*)

#### Applicazione
$$
\cfrac{Σ🢒e⇒〈x,t,Δ〉 \quad Σ🢒e'⇒v \quad Δ[x↦v]🢒t⇒v'}{Σ🢒e\:e'⇒v'}
$$

##### Applicazione ricorsiva
$$
\cfrac{Σ🢒e⇒〈f,x,t,Φ〉 \quad Σ🢒e'⇒v \quad Φ[f↦〈f,x,t,Φ〉][x↦v]🢒t⇒v'}{Σ🢒e\:e'⇒v'}
$$

#### "Esecuzione" variabile
$$
\cfrac{}{Σ🢒x⇒Σ(x)}
$$

## Eval

$eval:exp→val\:env→val$

```OCaml
let rec eval e s = match e with
    | Add(e1,e2) ->
	    let v1 = eval e1 s
	    and v2 = eval e2 s
	    in int_plus v1 v2
	| Let(x,e1,e2) ->
	    let v = eval e1 s
	    in eval e2 (bind s x v)
	| LetRec(f,x,e1,e2) -> eval e2 (bind s f ClosureRec(f,x,e1,e2))
	| Lam(x,e) -> Closure(x,e,s)
	| App(e1,e2) ->
	    let clos = eval e1 s
	    and v = eval e2 s
	    in match clos with
	        | Closure(x,t,p) -> eval t (bind p x v)
	        | ClosureRec(f,x,t,p) -> eval t (bind (bind p x v) f ClosureRec(f,x,t,p))
	        | _ -> error
	(*...*)

let intplus v1 v2 = match v1, v2 with
    | Int n1, Int n2 -> Int(n1+n2)
    (*...*)
```

## [[Tipi#^4de39f|Record]]

$$
\cfrac{∀i∈[1,k].Σ🢒e_i:v_i}{Σ🢒[l_1e_1,…,l_k:e_k]⇒[l_1:v_1,…,l_k:v_k]}
$$

$$
\cfrac{Σ🢒e⇒[l_1:v_1,…,l_k:v_k]\quad 1≤j≤k}{Σ🢒e.l_i⇒v_i}
$$

### Implementazione

```OCaml
type label = Lab of string
type exp = (*...*)
    | Record of (label * expr) list
    | Select of expr * label

(* Record[(Lab "size", Int 7); (Lab "weight", Int 255)] *)
```

### Funzioni di valutazione

```OCaml
(* Cerca un membro nel record *)
let rec lookupRecord recordbody (Lab l) =
    match recordbody with
        | [] -> raise FieldNotFound
        | (Lab l', v)::t -> if l = l' then v else lookupRecord t (Lab l)

(* Elabora tutte le espressioni del record *)
let evalRecord recordbody = match recordbody with
    | [] -> []
    | (Lab l, e)::t -> (Lab l, eval e)::(evalRecord t)

let rec eval e s = match e with
    (*...*)
	| Record(rbody) -> Record(evalRecord rbody)
    | Select(e', l) -> match eval e' s with
        | Record(rbody) -> lookupRecord rbody l
        | _ -> raise TypeMismatch
```

### [[Tipi#^5d3e5a|Polimorfismo]]

Una funzione definita come `(fun r: [x: Int] = r.x)` prende un record con un campo di nome `x` e restituisce il valore associato al campo di nome `x`. Possiamo applicarla all'argomento `[x:0]`.
`App((fun r: [x: Int] = r.x), [x:0]) -> 0`

Quindi, si può fare la stessa cosa con il record `[x: 0, y: 1]`, dato che `[x: Int, y: Int] <: [x: Int]`? In teoria sì, l'analisi statica potrebbe non accettarlo [[Tipi#^5ce74b|perché non è lo stesso tipo]], a meno che non sia implementata la regola di subsumption..