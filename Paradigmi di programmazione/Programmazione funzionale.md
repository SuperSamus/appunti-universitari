# Programmazione funzionale

- Si può programmare solo con #espressioni
- Computazione = riscrittura di espressioni

`map f(map g xs) = map(f*g)xs`

$[x_1,…,x_n] \rightarrow [g(x_1),…,g(x_n)] \rightarrow [f(g(x_1)),…,f(g(x_n))$

Si evitano effetti collaterali.

- Dichiarativi
	- Esempio: `FACT n = if n == 0 than 1 else n + FACT(n - 1)`
	- Non ci preoccupiamo di descrivere i passaggi in memoria, lo fa la macchina
- Espressioni = Funzioni
- Ricorsione
- [[λ-calcolo]]

## Astrazione

$\{x|\varphi (x)\}$