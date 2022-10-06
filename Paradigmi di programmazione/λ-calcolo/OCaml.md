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

### Regole di introduzione:
$$
\frac{}{Γ,x:z⊢x:z} \\
\frac{}{Γ⊢\underline{n}:\text{num}} \\
\frac{}{Γ⊢"s":str}
$$
### Regole di eliminazione

$$
\frac{Γ⊢e_1:\text{num} \quad Γ:e_2:num}{Γ⊢e_1+e_2:\text{num}} \\
\frac{Γ⊢e_1:\text{str} \quad Γ:e_2:str}{Γ⊢e_1\textasciicircum e_2:\text{str}} \\
Γ⊢e_1:z\\
\frac{Γ,x:z⊢e_2:σ}{Γ⊢\text{let }x=e_1 \text{ in } e_2:σ} \\
\frac{}{Γ,x:z⊢x:z} \\
\frac{}{Γ⊢\underline{n}:\text{num}} \\
\frac{}{Γ⊢"s"::\text{str}} \\
$$