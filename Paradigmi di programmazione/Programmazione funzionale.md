# Programmazione funzionale

- Diversamente dalla [[programmazione imperativa]], non c'è bisogno di *stato* o *memoria*
	- Niente variabili mutabili
- Programma = **espressioni**
	- Niente istruzioni
- Computazione = riscrittura di espressioni

Si evitano *effetti collaterali*.

- Le espressioni rappresentano *funzioni*
- Programmazione *dichiarativa*
	- Non ci preoccupiamo di descrivere i passaggi in memoria, lo fa la macchina
- Ricorsione
- [[λ-calcolo]]

$E::=0|1|...|true|false|E+E|E*E|\text{if } E \text{ then } E \text{ else }e|\text{fun } x \Rightarrow E| e(E)|...$

Esempio fattoriale:

```
FACT = fun n => if (n == 0) then 1 else n + FACT(n - 1)
```

(fun x => e)(a) -> e[a/x]

- `map f(map g xs)` = `map(f*g)xs`
	- $[x_1,…,x_n] \rightarrow [g(x_1),…,g(x_n)] \rightarrow [f(g(x_1)),…,f(g(x_n))$


## Astrazione

$\{x|\varphi (x)\}$
