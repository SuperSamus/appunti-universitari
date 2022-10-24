# Memoria

Vettore di parole (da 32 bit)
- `write(i,x)` scrivi nell'indirizzo `i` il contenuto `x`
- `read(i)` leggi il contenuto nell'indirizzo `i`

Implementazione:

```mermaid
flowchart TB
r1[reg] & r2[reg] & r3[reg] & r4[reg] --> Demux
Ind -- /2 --> Demux
WE -- /1 --> Mux
Mux & In --> r1[reg 00] & r2[reg 01] & r3[reg 10] & r4[reg 11]
Ind -- /2 --> Mux
```

Esempio: `write(2, 12)`
- `In=1100` (che finisce su tutti gli ingressi dei registri)
- `Ind=10`
- 


Questo è estremamente costoso, soprattutto con così tanti registri. Inoltre, dato che i [[Porte logiche#^b31833|Multiplexer]] costano più dei [[Porte logiche#^5e85c1|Demultiplexer]], leggere richiede più tempo che scrivere.

Altro design TODO:

```mermaid
flowchart LR

```

RAM: Random Access Memory
- Dinamiche
	- Va "rinfrescato" (leggendolo) periodicamente
- Statiche
	- Mantiene l'informazione se alimentato

TODO