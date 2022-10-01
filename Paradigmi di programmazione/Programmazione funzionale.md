# Programmazione funzionale

- Diversamente dalla [[programmazione imperativa]], non c'è bisogno di *stato* o *memoria*
	- Niente variabili mutabili
- Programma = **espressioni**
	- Niente istruzioni
	- Due espressioni/programmi sono uguali se calcolano lo stesso risultato
- Computazione = riscrittura di espressioni

Non ci sono [[β-riduzione#^b5ae66|effetti collaterali]].

- Le espressioni rappresentano *funzioni*
- Programmazione *dichiarativa*
	- Non ci preoccupiamo di descrivere i passaggi in memoria, lo fa la macchina
- Basato sul [[λ-calcolo]]
	- [[Sostituzioni|Passaggio per nome/valore]]
	- Esecuzione: [[β-riduzione]]

$E::=0|1|…|true|false|E+E|E*E|\text{if } E \text{ then } E \text{ else }E|ife(E,E,E)\text{fun } x \Rightarrow E| EE|\text{let } x=E \text{ in }E'|\text{ricorsione}|…$

## Esempi

### Fattoriale:

```
FACT = fun n => if (n == 0) then 1 else n + FACT(n - 1)
// (fun x => e)(a) -> e[a/x]
// FACT(3) = (fun n => if(n==0,1,n*FACT(n-1)))(3)
// -> ife(3==0,1,3*FACT(3-1))
// -> ife(false,1,3*FACT(3-1))
// -> 3*FACT(3-1)
// -> 3*FACT(2)
// = 3*(fun n => ife(...))(2)
// ...
// -> 3 * 2 * 1
// -> 6
```

### Map

```
map f(map g x) // = map(f∘g)x
```

$\text{map } f(\text{map } g([x_1,…,x_n])) \rightarrow^\star \text{map } f [g(x_1),…,g(x_n)] \rightarrow^\star [f(g(x_1)),…,f(g(x_n))$
### Let

```

```