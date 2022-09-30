# Macchina di Turing

Quintupla $<Q,a,b,x,S>$
- Stato
- Simbolo
- Scrivo b
- Sposto il nastro: sinistra/destra/fermo
- Arriva allo stato S.

$f: \mathbb{N} \rightharpoonup \mathbb{N} \; \text{calcolabile} \Leftrightarrow \exists M. \forall n \in \mathbb{N} \quad M(n) \downarrow \land M(n) = m \Leftrightarrow f(n) \downarrow \land f(n)=m$

Una funzione f è calcolabile se e solo se esiste una macchina di Turing in grado di implementare in tempo finito ($\downarrow$).

## Halting problem

Problema: nell'insieme delle funzioni parziali esistono funzioni non calcolabili.

Immagino una funzione che prende una macchina di Turing e restituisce un numero: se si può fare, tutti gli elementi della quintupla sono finiti. (E si può fare anche l'inverso)

Halting problem: questo problema è indecidibile.

$$
f(n) =
  \begin{cases}
    M_n(n) \downarrow \\
    \uparrow
  \end{cases}

$$

## Ogni macchina ha un programma

Esiste una macchina di Turing $M$ universale $U$.

$U(n,m) \rightarrow M_n(m)$

### Macchina

- Macchina (hardware)
- Istruzione (programma)
- Input/dati

Dati $\equiv$ Programma

#### Macchina programmabile

- Interprete
- Programma memorizzato

C'è anche bisogno di:

- Memoria (dati programmi)
- CPU
- Istruzioni