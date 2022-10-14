# OCaml

$ML→CAML→OCaml$

Linguaggio compilato in bytecode, eseguito da un interprete (per le $→_β$).

Consente di scrivere:

```OCaml
(* Dichiarazioni *)
let eta = 18;;
let anno: int = 2022;;
(* Espressioni *)
eta * anno;;
```

## Tipi di base

- int
- unit
- float
- bool
- char
- string

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
fun x -> t: int -> int;;
(fun x -> t) s u;;
fun x -> fun y -> x + y;; (* equivalente a... *)
fun x y -> x + y;;
```

## Let

%%
$\text{let }x=t;;→〈Σ,s〉$
TODO: Può il professore non cancellare il secondo dopo?
$$
\cfrac{}{}
$$
%%
