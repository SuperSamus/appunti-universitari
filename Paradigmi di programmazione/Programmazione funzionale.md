# Programmazione funzionale

- Diversamente dalla [[programmazione imperativa]], non c'è bisogno di *stato* o *memoria*
	- Niente variabili mutabili
- Programma = **espressioni**
	- Niente istruzioni
- Computazione = riscrittura di espressioni

Si evitano *effetti collaterali*.

- Le espressioni rappresentano *funzioni*
- Programmazione *dichiarativa*
	- Esempio: `FACT n = if n == 0 than 1 else n + FACT(n - 1)`
	- Non ci preoccupiamo di descrivere i passaggi in memoria, lo fa la macchina
- Ricorsione
- [[λ-calcolo]]

`map f(map g xs) = map(f*g)xs`

$[x_1,…,x_n] \rightarrow [g(x_1),…,g(x_n)] \rightarrow [f(g(x_1)),…,f(g(x_n))$

## Astrazione

$\{x|\varphi (x)\}$
