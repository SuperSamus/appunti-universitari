# Procedura di calcolo

Dati in input -> Dati in output

- $f: \mathbb{N} \rightarrow \mathbb{N}$ **NO**
    - Procedure troppo restrittive, non possono non ritornare niente.
- $f: \mathbb{N} \rightharpoonup \mathbb{N}$
    - Funzione parziale

Ma tutte le funzioni parziali sono calcolabili? Ce ne sono troppe… Alcune funzioni sono calcolabili:

1. Funzioni elementari (come $Successore$)
2. $f,g \; \text{calcolabili} \Rightarrow g \circ f \; \text{calcolabili}$
3. Funzioni ricorsive (che comprendono tra l'altro 1. e 2.)

Per loro: $[\mathbb{N} \rightharpoonup \mathbb{N}] \supseteq Ricorsive$

Questo è un approccio. Approcci sono:

1. Funzioni ricorsive
2. Church (λ-calcolo)
3. Turing
    - Algoritmo = Regola che una persona può seguire in modo meccanico e preciso