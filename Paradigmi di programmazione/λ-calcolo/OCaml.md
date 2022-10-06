# OCaml

$ξ∋e::=x|\underline{n}|"s"|e+e|e*e|e\textasciicircum e|\text{let }x=e \text{ in }e$

$P=\{e∈E|FV(e)=∅\}$

$e=_αe'$

$$
\text{let }x=e \text{ in }e \\
=_α \\
\text{let }y=e \text{ in }e'[y/x] \\
y \not ∈ FV(e')
$$

Esempi di programmi:

```ocaml
let x = 3+2 in
let y = 5+2 in
x+y
```

Errore di sintassi:

```
let x = "ciao" in
let y = 0 in
y^x
```

## Tipi
$τ ∋ z::=num|str$

$e:z$

Giudizio di tipo: $Γ⊢e:z$

$$
\frac{e_1:num \quad e_2:num}{e_1+e_2:num}
$$

$(Γ,e,z)→Γ⊢e:z$

$Γ,e→z \text{ t.c. } Γ⊢e:z$

Regole di introduzione