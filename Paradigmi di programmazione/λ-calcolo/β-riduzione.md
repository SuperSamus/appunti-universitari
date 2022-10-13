# β-riduzione

La più importante regola di riscrittura del [[λ-calcolo]].

$(λx.t)s →_β t[s/x]$

(Redex → Contractum)

Formalmente, la relazione $→_β ⊆ Λ ⨉ Λ$

$$
\cfrac{}{(λx.t)s →_β t[s/x]}
$$

$$
\cfrac{t →_β s}{tu →_β su} \quad \cfrac{t →_β s}{ut →_β us} \quad
\cfrac{t →_β s}{λx.t →_β λx.s}
$$

## Esempi

$(λx.x(xy))t →_β t(ty)$

La β-riduzione non è deterministica nei passaggi:

%%
$A=(λx.(λy.yx)z)v$

$B=(λy.yv)z$

$C=(λx.zx)v$

$D=zv$
%%

```mermaid
flowchart LR
A["(λx.(λy.yx)z)v"] --> B["(λy.yv)z"] --> D[zv]
A --> D
A --> C["(λx.zx)v"] --> D
```

La β-riduzione, nonostante il nome, può *allungare* l'espressione. Ciò può rendere difficile ottimizzare questo processo per i calcolatori.

Per esempio:

- $Δ = (λx.xx)$
- $Δ t →_β tt$
- $Ω = Δ Δ →_β Δ Δ →_β …$

Altro esempio:

- $k = λx.y$
- $kΩ = (λx.y)(Δ Δ)$

```mermaid
flowchart LR
A[kΩ] --> A & y
```

## Teorema di Church-Rosser

$t →_β^* s_1 ∧ t →_β^* s_2 ⇒ ∃ u. s_1 →_β^* n ∧ s_2 →_β^* u$

```mermaid
flowchart LR
t --> s1 & s2 -.-> u
```

Se:
- $t →_β^* s_1$
- $t →_β^* s_2$
- $s_1,s_2 ∈ NF$

Allora $s_1=_α s_2$.

### Corollario 1

Unicità forme normali (modulo $=_α$).

### Corollario 2

$t =_β s ⟺ ∃ u.t →_β^* u _β^*← s$

### Corollario 3

L'ordine delle β-riduzioni è irrilevante.

Ciò rende facilmente parallelizzabile il λ-calcolo.

## β-conversione

$(λx.t)s=_β t[s/x]$

$t=_β s ⟺ t (_β ← u →_β)^* s$

## Forma normale

Un termine è in forma normale se non si può β-ridurre.

Un termine $t$ ha una forma normale se esiste un termine $s$ tale che $t$ β-riduce ad $s$ in un numero finito di passi.

$∃ s ∈ NF.t \longrightarrow^*_β s$.

## Effetti collaterali

^b5ae66

Un effetto collaterale è un qualsiasi cosa che fa sì che il programma non sia una catena di β-riduzioni.

Se due espressioni hanno effetti collaterali, allora non possono mai essere uguali.

Esempio: $e_1+e_2=e_2+e_1$ sono uguali, ma non se ci sono effetti collaterali:
- $e_1≜print(a);return(2)$
- $e_2≜print(b);return(3)$
- $e_1+e_2$ scrive $ab$, poi ritorna $5$
- $e_1+e_2$ scrive $ba$, poi ritorna $5$

### Trasparenza referenziale

L'assenza di effetti collaterali, dove se $e →^* v$ allora usare $v$ o $e$ non fa differenza.
