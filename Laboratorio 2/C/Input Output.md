# I/O

- Libreria standard: `stdio`
    - `printf()`: scrive su `stdout`
        - Può contenere segnaposti `%…` per includere valori di variabili
    - `scanf()`: legge da `stdin`
        - Prende anche degli [indirizzi](puntatori) (`&`) delle variabili dove salvare i valori letti
        - Restituisce il numero di argomenti per cui l'input è valido
        - `*` gli fa ignorare la parte invalida dell'input
        - Si possono usare espressioni regolari

### Segnaposti (dopo `%`)

- Interi decimali: `d`, `u` (unsigned)
    - Si può anteporre `l` (long) o `h` (short)
- Double floating point `f`
- Carattere `c`
- Stringa `s`

## File

In C i file sono visti come *stream* (flussi di dati) da una fonte a una destinazione.

La libreria `stdio.h` ha funzionalità come:
- Struct `FILE`
- Costante `EOF`
- Stream `stdin`, `stdout`, `stderr`
- Funzioni come `fopen`, `fclose`

### Lettura

- `fgetc` legge un carattere e lo restituisce
- `fscanf` simile a `scanf`
- `fgets` legge al massimo `n-1` carattteri e li salva in `str`

#### Tipi di file

Bisogna leggerli con la stessa rappresentazione con cui sono stati scritti

- Testuali
- Binari