# OCaml

$ℰ∋e::=x|\underline{n}|\textquotedblleft s \textquotedblright|e+e|e*e|e\textasciicircum e|\text{let }x=e \text{ in }e$

$P=\{ℰ∈E|FV(e)=∅\}$

$e=_αe'$

$$
\text{let }x=e \text{ in }e' \\
=_α \\
\text{let }y=e \text{ in }e'[y/x] \quad y \not ∈ FV(e')
$$

Esempi di programmi:

```ocaml
let x = 3+2 in
let y = 5+2 in
x+y
```

## Tipi

Errore di semantica statica (non serve eseguire il programma per riceverlo):

```
let x = "ciao" in
let y = 0 in
y^x
```

**Sistema di tipi**: un meccanismo che impone vincoli sulla formazione delle frasi di un linguaggio per garantirne la sensatezza.

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
$$

### Assiomi

$$
\frac{}{Γ⊢\underline{n}:\text{num}} \\
\frac{}{Γ⊢\textquotedblleft s \textquotedblright ::\text{str}} \\
$$
Inversione:
- Se $Γ⊢e:z$, allora
	- Se $e=e_1+e_2$, abbiamo:
		- $z=\text{num} \quad Γ⊢e_1:\text{num} \quad Γ⊢e_2:\text{num}$

Unicità:
TODO

## TI (Type Inference)

Input $(Γ,e)

Output

TODO: sigh… È il professore capace di non scrivere in modo disordinato a far capire bene di cosa sta parlando?
