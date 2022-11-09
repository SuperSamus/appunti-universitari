# Assembly

Linguaggio di programmazione simile alla rappresentazione binaria della macchina, e viene compilato in linguaggio macchina.

## Microarchitettura

ARM: Advanced RISC Machine

RISC: Reduced Instruction Set Computer

Principi:
- Regolarità ⇒ Semplicità
- Caso comune ⇒ Veloce
- Piccolo è bello
- Buon progetto ⇔ Buoni compromessi

### Registri (ARMv7)

16 registri da 32 bit.

- R0-R3 temporanei
	- R0 output delle chiamate
	- R1-R3 parametri delle chiamate
- R4-R11 saved vars
- R12 temporaneo
- R13 SP (Stack Pointer)
- R14 LR (Link Register, l'indirizzo di ritorno di una chiamata)
- R15 PC (Program Counter)

### Memoria

ARM è [[Bit#^32cef1|Little Endian]].

- `LDR(B)` (Load register) M→R
- `STR(B)` (Store register) R→M

Tutte le istruzioni sono in memoria, il program counter tiene traccia dell'istruzione da eseguire, e dopo averla eseguita, aumenta del numero di byte da cui sono composte le istruzioni (4 se a 32 bit).

### ISA (Instruction Set Architecture)

Istruzioni di:
- Operative
- Memoria
- Salto

#### Operative (Aritmetico/Logiche)

Operandi: Dest Src1 Src2

Dest = Src1 *op* Src2

Src2 può quasi sempre essere anche una costante (`#N`).

- `ADD`
- `SUB`
- Shift (Src2 indica di quanti bit spostare)
	- Logical Shift (i bit vacanti vengono riempiti con `0`)
		- `LSL` (Logical Shift Left)
		- `LSR` (Logical Shift Right)
	- `ASR` (Arithmetic Shift Right) (dopo lo shift, il bit di segno viene copiato)
	- `ROR` (Rotate Right) (i bit vacanti vengono riempiti dai bit scartati)
- `BIC` (Bit Clear)
- Moltiplicazione
	- `MUL` Il risultato può andare in overflow
	- Se si vuole usare più registri (R1 e R2) per evitare l'overflow:
		- `SMULL` (Signed)
		- `UMULL` (Unsigned)
- FLAGS (variabili booleane, proprietà del risultato di un operazione)
	- `Z` Zero (vero se il risultato è uguale a `0`)
	- `N` Negativo (vero se il risultato è negativo)
	- `C` Carry (vero se ha avuto un riporto)
	- `V` Overflow (simile a `C`)
	- Settare
		- `CMP R1, R2` (R1-R2→FLAGS)
		- `ADDS R1, R2, R3` (→set FLAGS)
- Confronto (aggiungi `B` all'inizio per settare FLAGS)
	- `EQ`
	- `NE`
	- `GT`
	- `LT`
	- `GE`
- Salto
	- `B` Branch to label (fa puntare il program counter all'etichetta specificata)
	- `BL` (Prima copia l'indirizzo della prossima istruzione nel LR, poi fa branch)
- Utilizzo FLAGS
	- `ADDEQ`/`ADDNE`/`ADDLT` (fai l'addizione se `EQ` è vero)
	- `BEQ`/`BNE`/`BLT` (fai il branch se il rispettivo flag è vero)
- `MOV` copia i dati da un registro a un altro (oppure copia la costante nel registro)

## Esempi

### Aggiungi se pari

```
if (x pari) ++y;
```

`x` in R0, `y` in R1

Si vede se un bit è pari guardando il bit meno significativo.

```armasm
    LSL R0, R0 #31 # oppure AND R0, R0, #1
    CMP R0, #0
    BNE cout
    ADD R1, R1, #1
cout:
    /**/
```

Si poteva fare con meno istruzioni:

```armasm
    ANDS R0, R0, #1
    ADDEQ R1, R1, #1
cout:
    /**/
```

### Conta istanze

```
int count = 0;
for (int i = 0; i < n; ++i)
    if (v[i] == x) ++count
```

Nella memoria `v` (che parte dall'indirizzo in R0),  cercando `x` (R1) con `n` in R2, `count` in R3 e $i$ in R4:

```armasm
    MOV R3, #0
    Mov R4, #0
for:
    CMP R4, R2
    BEQ endfor
    LDR R5, [R0], #4 @ i numeri sono da 4 byte
    CMP R5, R1
    ADDEQ R3, R3, #1
    ADD R4, R4, #1
    B for
```

### Confronto stringhe

```
str1 = "abcd"; // Indirizzo parte da R0
str2 = "qztf"; // Indirizzo parte da R1
```

```armasm
loop:
    LDRB R4, [R0], #1
    LDRB R5, [R1], #1
    CMP R4, R5
    BLT
    BEQ loop
    B
```