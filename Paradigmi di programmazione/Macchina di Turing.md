# Macchina di Turing

Quintupla $<Q,a,b,x,S>$
- Stato
- Simbolo
- Scrivo b
- Sposto il nastro: sinistra/destra/fermo
- Arriva allo stato S.

$f: ℕ ⇀ ℕ \; \text{calcolabile} ⟺ ∃ M. ∀n ∈ ℕ \quad M(n) ↓ ∧ M(n) = m ⟺ f(n) ↓ ∧ f(n)=m$

Una funzione f è calcolabile se e solo se esiste una macchina di Turing in grado di implementare in tempo finito ($↓$).

## Halting problem

Problema: nell'insieme delle funzioni parziali esistono funzioni non calcolabili.

Immagino una funzione che prende una macchina di Turing e restituisce un numero: se si può fare, tutti gli elementi della quintupla sono finiti. (E si può fare anche l'inverso)

Halting problem: questo problema è indecidibile.

$$
f(n) =
  \begin{cases}
    M_n(n)↓ \\
    ↑
  \end{cases}

$$

## Ogni macchina ha un programma

Esiste una macchina di Turing $M$ universale $U$.

$U(n,m) → M_n(m)$

### Macchina

- Macchina (hardware)
- Istruzione (programma)
- Input/dati

Dati ≡ Programma

#### Macchina programmabile

- Interprete
- Programma memorizzato

C'è anche bisogno di:

- Memoria (dati programmi)
- CPU
- Istruzioni

Macchina astratta ≜ Insieme di funzionalità (strutture dati e algoritmi) che simulano il comportamento di una macchina fisica