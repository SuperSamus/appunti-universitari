# Memoria

Vettore di parole (da 32 bit)
- `write(i,x)` scrivi nell'indirizzo `i` il contenuto `x`
- `read(i)` leggi il contenuto nell'indirizzo `i`

Implementazione TODO:

```mermaid
flowchart TB
r1[reg] & r2[reg] & r3[reg] & r4[reg] --> Demux
Ind -- /2 --> Demux
WE -- /1 --> Mux --> r1 & r2 & r2 & r4
Ind -- /2 --> Mux
```

Questo è incridebilmente costoso. Dato che i [[Porte logiche]] costano più dei 