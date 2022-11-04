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

16 reg da 32 bit.

- R0-R3 temporanei
	- R0 output delle chiamate
	- R1-R3 parametri delle chiamate
- R4-R11 saved vars
- R13 temporaneo
- R13 SP (Stack Pointer)
- R14 LR (Link Register, l'indirizzo di ritorno di una chiamata)
- R15 PC (Program Counter)

### Memoria

ARM è 