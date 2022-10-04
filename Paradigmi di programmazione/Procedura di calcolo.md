# Procedura di calcolo

Dati in input -> Dati in output

- $f: ℕ → ℕ$ **NO**
    - Procedure troppo restrittive, non possono non ritornare niente.
- $f: ℕ ⇀ ℕ$
    - Funzione parziale

Ma tutte le funzioni parziali sono calcolabili? Ce ne sono troppe… Alcune funzioni sono calcolabili:

1. Funzioni elementari (come $Successore$)
2. $f,g \; \text{calcolabili} ⇒ g ∘ f \; \text{calcolabili}$
3. Funzioni ricorsive (che comprendono tra l'altro 1. e 2.)

Per loro: $[ℕ ⇀ ℕ] ⊇ Ricorsive$

Questo è un approccio. Approcci sono:

1. Funzioni ricorsive
2. Church ([[λ-calcolo]])
3. Turing
    - Algoritmo = Regola che una persona può seguire in modo meccanico e preciso