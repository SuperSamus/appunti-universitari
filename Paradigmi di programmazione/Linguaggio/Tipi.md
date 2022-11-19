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
- $Γ⊢e:τ \quad FV(e)⊆Dom(Γ)$
- $Γ(x)≜\text{il tipo di }x$

Per esempio: $x:str,y:str⊢x\textasciicircum y:str$

Proprietà da avere:
- Se il tipo viene dato, deve essere corretto: $(Γ,e,τ)→Γ⊢e:τ$
- Se il tipo non viene dato, deve poter essere trovato e corretto: $Γ,e→τ \text{ t.c. } Γ⊢e:τ$

### Unione disgiunta funzioni

$$
\begin{matrix} f:A→B \\ g:A'→B' \end{matrix} \quad A∩A'=∅ \quad f+g:A∪A'→B∪B' \quad (f+g)(x)≜\begin{cases} f(x) & \text{se } x∈A \\ g(x) & \text{se } x∈A' \end{cases}
$$

Utile quando si ha due ambienti diversi:

$$
(Γ+Δ)(x)≜\begin{cases} Γ(x) & \text{se } x∈Dom(Γ) \\ Δ(x) & \text{se } x∈Dom(Δ) \end{cases}
$$

### Regole di introduzione:

Valori: $E⊃V∋v::=x|\underline{n}|\textquotedblleft s \textquotedblright$

$$
\cfrac{}{Γ,x:τ⊢x:τ} \quad
\cfrac{}{Γ⊢\underline{n}:\text{nat}} \quad
\cfrac{}{Γ⊢\underline{b}:\text{bool}} \quad
\cfrac{}{Γ⊢\textquotedblleft s\textquotedblright:str}
$$

### Regole di eliminazione

$$
\cfrac{Γ⊢e_1:\text{nat} \quad Γ:e_2:nat}{Γ⊢e_1+e_2:\text{nat}} \quad
\cfrac{Γ⊢e_1:\text{str} \quad Γ:e_2:str}{Γ⊢e_1\textasciicircum e_2:\text{str}} \\
\cfrac{Γ⊢e_1:bool \quad Γ⊢e_2:τ \quad Γ⊢e_3:τ}{Γ⊢ite(e_1,e_2,e_3):τ} \quad
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

### Teorema indebolimento

$$
\cfrac{Γ⊢e:τ_2}{Γ,x:τ_1⊢e:τ_2}
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

Regole di eliminazione: dato in termine di un certo tipo, cosa ci si può fare ^5ce74b

$$
\cfrac{Γ⊢t:τ_1→τ_2 \quad Γ⊢s:τ_1}{Γ⊢t\:s:τ_2}
$$

Combiniamo le regole:

$$
\cfrac{\cfrac{Γ,x:τ_1⊢t:τ_2}{Γ⊢λx.t:τ_1→τ_2} \quad Γ⊢s:τ_1}{Γ⊢ts:τ_2}
$$

Abbiamo un β-redex!

## Record

^4de39f

$$
\cfrac{∀i∈[1,k].Γ⊢e_i:τ_i}{[l_1e_1,…,l_k:e_k]→[l_1:τ_1,…,l_k:τ_k]}
$$

$$
\cfrac{Γ⊢e:[l_1:τ_1,…,l_k:τ_k]\quad 1≤i≤k}{Γ⊢e.l_i:τ_i}
$$

## [[Programmazione orientata agli oggetti|Oggetti]]

### Polimorfismo nello structural subtyping

^5d3e5a

Una funzione è polimorfa se ha la caratteristica di essere applicabile ad argomenti di tipo diverso.

Più in generale: il polimorfismo per sottotipo si basa sull'assunzione che valori di un tipo $τ_1$ possano sempre essere usati al posto di valori di un altro tipo $τ_2$. Se $τ_1$ è sottotipo di $τ_2$, si scrive $τ_1<:τ_2$.

Un sistema di tipi che consente al tipo $τ_1$ di assere considerato anche di tipo $τ_2$ usa la regola di **subsumption**:

$$
\cfrac{Γ⊢e:τ_1\quad τ_1<:τ_2}{Γ⊢e:τ_2}
$$

#### Definendo $<:$ con i record:

$$
\cfrac{}{[l_1:τ_1,…,l_n:τ_n,…,l_{n+k}:τ_{n+k}]<:[l_1:τ_1,…,l_n:τ_n]}
$$

L'ordine dei campi non importa:

$$
\cfrac{[l_1:τ_1,…,l_n:τ_n] \text{ permutazione di }[l'_1:τ'_1,…,l'_n:τ'_n]}{[l_1:τ_1,…,l_n:τ_n]<:[l'_1:τ'_1,…,l'_n:τ'_n]}
$$

Il sottotipo può anche operare in "profondità":

$$
\cfrac{∀i.τ_i<:τ'_i}{[l_1:τ_1,…,l_n:τ_n]<:[l'_1:τ'_1,…,l'_n:τ'_n]}
$$

Quindi, per esempio, $[x:nat,y:[a:nat]]

### Type weakening

```OCaml
let s = object
    val mutable v = []

    method pop = (* *)
    method push hd (* *)
end ;;
```

Se `v` fosse iniziato con qualcosa come `[0; 2]` avrebbe tipo `<pop: int option; push: int -> unit>`

Che succede invece se nell'oggetto `s` inizializziamo `v` come lista vuota? Che tipo viene inferito?

`< pop: '_weak option; push: '_weak -> unit >`

Il tipo inferito contiene variabili di tipo, ma non è veramente polimorfo. Benché sia mutabile, `v` non potrà avere tipi diversi in momenti diversi dell'esecuzione. Il tipo sarà ricalcolato appena possibile, andando ad istanziare definitivamente la variabile provvisoria con un tipo concreto.
