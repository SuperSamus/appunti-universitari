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

### ISA (Instruction Set Architecture)

Istruzioni di:
- Operative
- Memoria
- Salto

#### Operative (Aritmetico/Logiche)

Operandi: Dest Src1 Src2

Dest = Src1 *op* Src2

Src2 può essere anche una costante.

- `ADD`
- `SUB`
- Shift (Src2 indica di quanti bit spostare)
	- Logical Shift (i bit vacanti vengono riempiti con `0`)
		- `LSL` (Logical Shift Left)
		- `LSR` (Logical Shift Right)
	- `ASR` (Arithmetic Shift Right) (dopo lo shift, il bit di segno viene copiato)
	- `ROR` (Rotate Right) (i bit vacanti vengono riempiti dai bit scartati)
- `BIC`
- Moltiplicazione
	- `MUL` Il risultato può andare in overflow
	- Se si vuole usare più registri (R1 e R2) per evitare l'overflow:
		- `SMULL` (Signed)
		- `UMULL` (Unsigned)