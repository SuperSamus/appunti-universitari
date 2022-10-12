# OCaml

$E∋e::=x|\underline{n}|\textquotedblleft s \textquotedblright|e+e|e*e|e\textasciicircum e|\text{let }x=e \text{ in }e$

$P=\{e∈E|FV(e)=∅\}$

$e=_αe'$

$$
\text{let }x=e \text{ in }e' \\
=_α \\
\text{let }y=e \text{ in }e'[y/x] \quad y ∉ FV(e')
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

$Τ ∋ τ::=num|str$

$e:τ$

Per esempio:

$$
\frac{e_1:num \quad e_2:num}{e_1+e_2:num}
$$

Questi sistemi servono a prevenire operazioni come $ADD \: ADD \: ADD$ (che il λ-calcolo non previene in nessun modo).

### Giudizi di tipo

$e$ può essere tante cose (come un segnaposto), quindi $e:τ$ da solo non basta.

Ci vuole quindi un ambiente: $Γ::=x_1:τ_1,…,x_n:τ_n$, dove $Γ⊢e:τ$.

Per esempio: $x:str,y:str⊢x\textasciicircum y:str$

Proprietà da avere:
- Se il tipo viene dato, deve essere corretto: $(Γ,e,τ)→Γ⊢e:τ$
- Se il tipo non viene dato, deve poter essere trovato e corretto: $Γ,e→τ \text{ t.c. } Γ⊢e:τ$

#### Regole di introduzione:

Valori: $E⊃V∋v::=x|\underline{n}|\textquotedblleft s \textquotedblright$

$$
\frac{}{Γ,x:τ⊢x:τ} \\
\frac{}{Γ⊢\underline{n}:\text{num}} \\
\frac{}{Γ⊢\textquotedblleft s\textquotedblright:str}
$$

#### Regole di eliminazione

$$
\frac{Γ⊢e_1:\text{num} \quad Γ:e_2:num}{Γ⊢e_1+e_2:\text{num}} \\
\frac{Γ⊢e_1:\text{str} \quad Γ:e_2:str}{Γ⊢e_1\textasciicircum e_2:\text{str}} \\
\frac{Γ⊢e_1:τ \quad Γ,x:τ⊢e_2:σ}{Γ⊢\text{let }x=e_1 \text{ in } e_2:σ}
$$

#### Teorema inversione

Se $Γ⊢e:τ$, e se $e=e_1+e_2$, abbiamo:

$τ=\text{num} \quad Γ⊢e_1:\text{num} \quad Γ⊢e_2:\text{num}$

Lo stesso modo per tutti i costruttori.

#### Teorema unicità

$∀e.∀τ. \text{ esiste al massimo in tipo } t \text{ t.c } Γ⊢e:τ$

#### Teorema sostituzione

$$
\frac{Γ,x:τ⊢e:σ \quad Γ⊢e':τ}{Γ⊢e[e'/x]:σ}
$$

### Algoritmo TI (Type Inference)

Input: $(Γ,e)$

Output: $τ \text{ t.c. } Γ⊢e:τ \text{ se esiste, fail altrimenti}$

```
case e of
    e==n => τ ≜ num
    e=="s" => τ ≜ str
    e==x => if (x:τ)∈Γ then τ else fail
```

Esempio:

```
e=let x = e1 in e2
    => if TI(Γ, e1) == τ
        then if TI(Γ,x:τ,e2) == σ
        then σ
        else fail
    else fail
```

Complessità: lineare.

### Type safety

Se l'espressione è tipabile, si può eseguire.

#### Progress

$$
\frac{Γ⊢e:τ \quad e→e'}{Γ⊢e':τ}
$$

#### Preservation

Se $Γ⊢e:τ$ allora una delle due:
- $e=v$ valore
- $∃e':e→e'$
