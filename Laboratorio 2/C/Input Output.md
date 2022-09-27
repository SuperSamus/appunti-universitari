# I/O

- Libreria standard: `stdio`
    - `printf()`: scrive su `stdout`
        - Può contenenere sengaposti `%…` per includere valori di variabili
    - `scanf()`: legge da `stdin`
        - Prende anche degli indirizzi (`&`) delle variabili dove salvare i valori letti
        - Restituisce il numero di argomenti per cui l'input è valido
        - `*` gli fa ignorare la parte invalida dell'input
        - Si possono usare espressioni regolari

### Segnaposti (dopo `%`)

- Interi decimali: `d`, `u` (unsigned)
    - Si può anteporre `l` (long) o `h` (short)
- Double floating point `f`
- Carattere `c`
- Stringa `s`