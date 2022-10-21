# OCaml

$ML→CAML→OCaml$

Linguaggio [[Programmazione funzionale|funzionale]] compilato in bytecode, eseguito da un interprete (per le $→_β$).

Consente di scrivere:

```OCaml
(* Dichiarazioni *)
let eta = 18;;
let anno: int = 2022;;
(* Espressioni *)
eta * anno;;
```

## [[Tipi]] di base

- int
- unit
- float
- bool
- char
- string
- T list

### Casting

int + float (come `3 + 3.2`) non si può fare implicitamente:

$$
\cfrac{Γ⊢t:int \quad Γ⊢s:int}{Γ⊢t+s:int}
$$

Bisogna usare funzioni come `int_to_float` o `float_to_int` per convertire esplicitamente da un tipo all'altro (es. `(int_to_float 3) + 3.2 : float`.

### Tipi composti

$T→S$

$T_1*T_2*…*T_n$ (*tuple*)

Per esempio:
```OCaml
let x: int*bool*string = (10, true, "hello");;
fun x -> t: int -> int;; (* x non affilato con il precedente *)
(fun x -> t) s u;;
fun x -> fun y -> x + y;;
(* equivalente a... *) fun x y -> x + y;;
```

## Let

$\text{let }x=t;;→〈Σ,s〉$

$$
\cfrac{〈Σ,t〉→〈Σ',v〉}{〈Σ,\text{let }x=t;;〉→〈Σ',x↦v〉}
$$

Permette anche di destrutturare le tuple:
```OCaml
let p: float*float = (.2, .3);;
let (x, y) = p in x + y
```

%%
```OCaml
fun f n -> f n + 1;;
f (fun (x,y) -> x + y) (2,3)
```
Il risultato è 6.
%%

TODO:
Si è visto che esistono tipi $'a→int$, (tipi generici, inferiti automaticamente).
L'istanziazione non è esplicita, ma automatica.

Zucchero sintattico:
```OCaml
let id (x: int) = x (*int -> int*)
(* let id = fun (x:int) -> x *)
```

Esempi:

```OCaml
let scambia (x,y) = (y,x) (* 'a*'b -> 'b*'a *)
(* let scambia = fun (x,y) -> (y,x) *)

let scambia_add (x,y) = (y+5,x+5) (* -> int *)
(* +: int -> int *)
```

---

```OCaml
let maggiore x y = if x > y then x else y
```

Che tipo sono $'a → 'b → ?$? Abbiamo questi vincoli:
- `if else` fa sì che $'a='b$, quindi $'a→'a→'a$
- $>:'a→'a→bool$, tuttavia `>` non si può fare su tutti i tipi (come le funzioni)
	- OCaml *non* previene l'utilizzo di tipi incompatibili, prende solo il tipo più generico possibile, che vuol dire che si può avere errori di runtime (altri linguaggi come Haskell o Rust invece hanno meccanismi per prevenirlo)

## Liste

Lista ≜ Sequenza *finita*, *ordinata* e *immutabile* di espressioni *dello stesso tipo* (mentre le tuple possono avere i tipi che vogliono)

```OCaml
[1;2;3]: int list
[true;true && false]: bool list
[]: 'a list
[[2;3];[3;4];[]]: (int list) list
```

Che tipo è questo?
```OCaml
[[];[fun x -> x]]
```

Vincoli:
- Il primo elemento `'a list`
- Il secondo elemento `'a->'a list`
- Combinandoli, si sceglie quello più restrittivo, quindi otteniamo `('a->'a list) list`

L'operatore *cons* crea una nuova lista, con un nuovo elemento di fronte alla lista:
```Ocaml
1 :: [2; 3] (* [1; 2; 3] *)
```

Per utilizzare gli elementi di una lista si usa il pattern matching:
```OCaml
let f (x:'a list) =
    match x with
        | [] -> (**)
        | y::ys -> (**)
```

Esempi con ricorsione:
```OCaml
let rec sum_list(xs: int list) =
    match xs with
        | [] -> 0
        | y::ys -> y + sum_list ys;;

let rec filter xs p =
    match xs with
        | [] -> []
        | y::ys -> if (p y) then y::(filter ys p) else (filter ys p);;

let rec append xs ys =
    match xs with
        | [] -> ys
        | z::zs -> z::(append zs ys)

let rec fold_left f a xs =
    match xs with
        | [] -> a
        | y::ys -> fold_left f (f a y) ys
```

$map:('a→'b)→'a \: list→'b \: list$

```OCaml
let rec map f xs =
    match xs with
        | [] -> []
        | y::ys -> (f y)::(map f ys);;
```
