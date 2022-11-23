Insieme di componenti hardware che implementano un interprete per un certo ISA (per esempio [[Assembly|ARMv7]]).

Deve essere implementato a livello hardware:

```
while (true) {
    fetch
    decode
    execute
    WB
}
```

Più gli stati necessari (come PC e REG).

Esempio implementazione Load e Store dalla [[Memoria]]:

```mermaid
flowchart LR

WE --> Multiplexer --> R0 & ... & R15
IndW["Ind(W)"] --> Multiplexer
IN --> R0 & ... & R15
R0 & ... & R15 ---> Demul1 & Demul2
IndR1["Ind(R)1"] --> Demul1
IndR2["Ind(R)2"] --> Demul2
Demul1 & Demul2 --> ...1[...]
```

Bisogna anche implementare un **ALU** (Arithmetic Logic Unit), che deve anche poter settare i FLAG.

Vediamo `ADD Ra, Rb, Rc`:

```mermaid
flowchart LR
PC --> IM[Instruction Memory]
IM --> |/4| ...
IM --> |Cond OP| ...
IM --> |/4| ...
IM --> |/4| Rs
IM --> |/4| Rd
IM --> |/4| Rsrc2
Rs & Rd & Rsrc2 --> REG
REG --> |SrcA| ALU+
REG --> |SrcB| ALU+
ALU+ --> FLAG
ALU+ --> |/32| REG
```
