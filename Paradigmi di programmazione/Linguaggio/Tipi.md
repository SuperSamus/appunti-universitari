# Tipi

Errore di semantica statica (non serve eseguire il programma per riceverlo):

```
let x = "ciao" in
let y = 0 in
y^x
```

**Sistema di tipi**: un meccanismo che impone vincoli sulla formazione delle frasi di un linguaggio per garantirne la sensatezza.

$Τ ∋ τ::=nat|str|bool|τ→τ$

$e:τ$

Per esempio:

$$
\cfrac{e_1:nat \quad e_2:nat}{e_1+e_2:nat}
$$

Questi sistemi servono a prevenire operazioni come $ADD \: ADD \: ADD$ (che il λ-calcolo non previene in nessun modo).

## Giudizi di tipo

$e$ può essere tante cose (come un segnaposto), quindi $e:τ$ da solo non basta.

Ci vuole quindi un ambiente/contesto (finito):
- $Γ:Var→Type$
- $Γ::=x_1:τ_1,…,x_n:τ_n$
- $Γ⊢e:τ$.

Per esempio: $x:str,y:str⊢x\textasciicircum y:str$

Proprietà da avere:
- Se il tipo viene dato, deve essere corretto: $(Γ,e,τ)→Γ⊢e:τ$
- Se il tipo non viene dato, deve poter essere trovato e corretto: $Γ,e→τ \text{ t.c. } Γ⊢e:τ$

### Regole di introduzione:

Valori: $E⊃V∋v::=x|\underline{n}|\textquotedblleft s \textquotedblright$

$$
\cfrac{}{Γ,x:τ⊢x:τ} \\
\cfrac{}{Γ⊢\underline{n}:\text{nat}} \\
\cfrac{}{Γ⊢\textquotedblleft s\textquotedblright:str}
$$

### Regole di eliminazione

$$
\cfrac{Γ⊢e_1:\text{nat} \quad Γ:e_2:nat}{Γ⊢e_1+e_2:\text{nat}} \\
\cfrac{Γ⊢e_1:\text{str} \quad Γ:e_2:str}{Γ⊢e_1\textasciicircum e_2:\text{str}} \\
\cfrac{Γ⊢e_1:τ \quad Γ,x:τ⊢e_2:σ}{Γ⊢\text{let }x=e_1 \text{ in } e_2:σ}
$$

### Teorema inversione

Se $Γ⊢e:τ$, e se $e=e_1+e_2$, abbiamo:

$τ=\text{nat} \quad Γ⊢e_1:\text{nat} \quad Γ⊢e_2:\text{nat}$

Lo stesso modo per tutti i costruttori.

### Teorema unicità

$∀e.∀τ. \text{ esiste al massimo in tipo } t \text{ t.c } Γ⊢e:τ$

### Teorema sostituzione

$$
\cfrac{Γ,x:τ⊢e:σ \quad Γ⊢e':τ}{Γ⊢e[e'/x]:σ}
$$

## Algoritmo TI (Type Inference)

Input: $(Γ,e)$

Output: $τ \text{ t.c. } Γ⊢e:τ \text{ se esiste, fail altrimenti}$

```
case e of
    e==n => τ ≜ nat
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

## Type safety

Se l'espressione è tipabile, si può eseguire.

### Progress

$$
\cfrac{Γ⊢e:τ \quad e→e'}{Γ⊢e':τ}
$$

### Preservation

Se $Γ⊢e:τ$ allora una delle due:
- $e=v$ valore
- $∃e':e→e'$

### Funzioni

Le funzioni sono tipi. Per esempio:
- $nat → bool$
- $nat → (nat → bool)$
- $(num→num)→(num→(num→num))$

Il corpo di una funzione non si tocca finché non viene chiamata.

### Costruttore/Distruttori

Regola di introduzione: come produrre valori di in certo tipo

$$
\cfrac{Γ,x:τ_1⊢t:τ_2}{Γ⊢λx.t:τ_1→τ_2}
$$

Regole di eliminazione: dato in termine di un certo tipo, cosa ci si può fare

$$
\cfrac{Γ⊢t:τ_1→τ_2 \quad Γ⊢s:τ_1}{Γ⊢ts:τ_2}
$$

Combiniamo le regole:

$$
\cfrac{\cfrac{Γ,x:τ_1⊢t:τ_2}{Γ⊢λx.t:τ_1→τ_2} \quad Γ⊢s:τ_1}{Γ⊢ts:τ_2}
$$

Abbiamo un β-redex!