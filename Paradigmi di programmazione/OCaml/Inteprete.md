# Interprete

$e::=true|false|n|o(e,e)|ite(e,e,e)$

$op::=+|\&|==$

$eval::exp→int$

$syntax::string→exp$

```mermaid
flowchart LR
L --> ASint --> AST1[AST] --> AStat[Analisti statica] --> TC[Type checking/inference] & CD[Controllo dinamico]
CD --> Eval --> Result
subgraph ASint[Analisi sintattica]
    subgraph AL[Analisi lessicale]
        Scanner --> TL[Token list]
    end
    subgraph AG[Analisi grammaticale]
        Parsed --> AST2[AST]
    end
end
```

Per esempio, la stringa $ite(3+2==5,0,1)$ viene alla fine tradotto in questo albero di derivazione astratta (AST):

```mermaid
flowchart TB
ite --> eq(==) & 0 & 1
eq --> + & 5
+ --> 3 & 2
```

## Sintassi in [[OCaml]]

### Scanner

Dalla stringa (di codice), genera i seguenti token:

```OCaml
type token =
    | Tkn_num of int
    | Tkn_op of string
    | Tkn_lpar
    | Tkn_rpar
    | Tkn_end

exception ParseError of string * string
```

Implementazione:

```OCaml
let scanner s =
    let rec scanner_rec s pos =
        if pos = String.length s then [Tkn_end]
        else
            let c = String.sub s pos 1
```

### AST

Generato grazie ai token:

```OCaml
type val =
    | Valb of bool
    | Valn of int

type op =
    | Add
    | And
    | Eq

type exp =
    | Val of val
    | Op of op * exp * exp
    | Ite of exp * exp * exp

eval(Ite(Op(Eq,Op(Add,Valn 3,Valn 2),Valn 5),Valn 0,Valn 1))
```

`eval` qui è definito come $eval:exp→val \; option$

```OCaml
let rec eval e =
    match e with
        | Val v -> Some v
        | Op(f,e1,e2) -> 
            let v1 = eval e1
            and v2 = eval e2
            in
            match v1,v2 with
                | None,_ | _, None -> None
                | Some w1, Some w2 ->
                    match f with
                        | Add -> match w1, w2 with
                            | Valn n1, Valn n2 -> Some Valn(n1+n2)
                            | _, _ -> None
(* ... *)
```

Inferenza di tipo

```OCaml
type ty =
    | Tybool
    | Tyint
```

```OCaml
let rec tyinf e =
    match e with
        | Val v -> match v with
            | Valb b -> Some Tybool
            | Valn n -> Some Tyint
        | Op (Add,e1,e2) ->
            let t1 = tyinf e1
            and t2 = tyinf e2
            in
            match t1,t2 with
                | Some Tyint, Some Tyint -> Some Tyint
                | _, _ -> None
(* ... *)
```

## Ottimizzazioni

^4a0b50

Grazie alla legge degli indiscernibili di Leibniz:

$e_1≈e_2⇒c[e_1]≈c[e_2]$

OCaml può applicare ottimizzazioni come questa:

$map \: f(map \: g \: xs) ≈ map (f∘g) xs$
