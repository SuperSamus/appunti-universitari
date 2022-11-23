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

Esempio implementazione [[Memoria]]:

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

Bisogna anche implementare un **ALU** (Arithmetic Logic Unit), che deve anche setta il .