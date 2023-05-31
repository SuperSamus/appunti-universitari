# Memoria

Vettore di parole (da 32 bit)
- `write(i,x)` scrivi nell'indirizzo `i` il contenuto `x`
- `read(i)` leggi il contenuto nell'indirizzo `i`

Esempio: `write(2, 12)`
- `In=1100` (che finisce su tutti gli ingressi dei registri)
- `Ind=10`, quindi `reg 10` sarà l'unico a ricevere `WE=1` (Write Enable), mentre tutti gli altri lo hanno a 0
- L'`OUT` di `Demux` è il contenuto di `reg 10`, quindi `1100`

Esempio in [[Verilog]]:
```verilog
reg[3:0] M[3:0];

assign out = M[IND];

always@(posedge clock)
    if(WE) M[IND]=IN;
```

Esempio implementazione:

```mermaid
flowchart TB
Ind --> |/2| Decode & Mux
WE --> |/1| Decode
Decode & In --> r1[reg 00] & r2[reg 01] & r3[reg 10] & r4[reg 11] --> Mux
```

Questo è estremamente costoso, soprattutto con così tanti registri. Inoltre, dato che i [[Porte logiche#^b31833|Multiplexer]] costano più dei [[Porte logiche#^5e85c1|Demultiplexer]], leggere richiede più tempo che scrivere.

Altro design:
![[Design memoria.excalidraw]]

Le bitline restituiscono i bit incidenti alla wordline corrispondente a `Ind`. Se le bitline sono accese, il bit viene anche scritto, se sono spente viene solo letto.

Questo design è di solito usato per le RAM: Random Access Memory
- Dinamiche
	- Va "rinfrescato" (leggendolo) periodicamente
- Statiche
	- Mantiene l'informazione se alimentato

Come si potrebbe combinare più moduli RAM (per esempio 2 moduli di RAM di 1GB di 8 bit)?
- Il bit più significativo indica il modulo, gli altri bit indicano l'indirizzo
	- Il primo modulo in questo caso occupa gli indirizzi $[0,2^{30})$, e il secondo $[2^{30}, 2^{31})$
	- Serve sempre un multiplexer per scegliere il modulo giusto
		- Dato che l'altro metodo non ha questo difetto, questo metodo non è mai usato nel mondo reale
- Gli altri bit indicano l'indirizzo, il bit meno significativo indica il modulo
	- Il primo modulo occupa gli indirizzi pari, il secondo gli indirizzi dispari, insieme $[0,2^{31})$
	- Se si vuole accedere a due indirizzi consecutivi (partendo da un indirizzo pari), non serve un multiplexer, e si risparmia un accesso

![[Moduli RAM.excalidraw]]

Esistono anche le ROM (Read Only Memory), ma negli incroci wordline/bitline c'è un fusibile bruciabile con corrente sulla wordline/bitline corrispondente: lasciarlo intatto equivale a 0, bruciarlo equivale a 1.

Ci sono anche le EEPROM (Electrically Erasable Programmable ROM), dove il fusibile è scrivibile un numero limitato di volte (più di uno almeno).

(Implementazioni non disegnate qui)