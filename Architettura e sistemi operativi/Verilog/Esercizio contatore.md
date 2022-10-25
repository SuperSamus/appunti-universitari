# Esercizio contatore

## Approccio strutturale

- Definiamo una codifica per i simboli di entrata e di uscita
- Costruiamo una macchina a stati finiti
- Deriviamo la tabella di verità delle transizioni di stato e delle uscite
- Ricaviamo la formula combinatorie per le uscite e per lo stato ovvero implementiamo un modulo Verilog per le uscite e per lo stato
- Determiniamo il numero di registri necessari in base agli stati da memorizzare, ovvero implementiamo un modulo registro in Verilog
- Connettiamo le reti combinatorie per realizzare la rete sequenziale, ovvero creiamo un `module` con componenti `wire` che invoca opportunamente gli altri moduli e definiamo il `module` `test`

Quindi:
- Ingressi $I=\{0,1\}$ Uscite $U=\{00,01,10,11\}$ Stati $S=\{S0,S1,S2,S3\}$
- Costruiamo la macchina a stati finiti

### Automa di Mealy

```mermaid
flowchart LR
S0 -- 0/00 --> S0
S0(((S0))) -- 1/01 --> S1
S1 -- 0/01 --> S1
S1((S1)) -- 1/10 --> S2
S2 -- 0/10 --> S2
S2((S2)) -- 1/11 --> S3
S3 -- 0/11 --> S3
S3((S3)) -- 1/00 --> S0
```

### Automa di Moore

```mermaid
flowchart LR
S0 -- 0 --> S0
S0(((S0/00))) -- 1 --> S1
S1 -- 0 --> S1
S1((S1/01)) -- 1 --> S2
S2 -- 0 --> S2
S2((S2/10)) -- 1 --> S3
S3 -- 0 --> S3
S3((S3/11)) -- 1 --> S0
```

### Tabella di verità

| $S1_{old}$ | $S0_{old}$ | $X$ | $S1_{new}$ | $S0_{new}$ | $z1$ | $z0$ |
| ---- | ---- | --- | ---- | ---- | ---- | ---- |
| 0    | 0    | 0   | 0    | 0    | 0    | 0    |
| 0    | 0    | 1   | 0    | 1    | 0    | 1    |
| 0    | 1    | 0   | 0    | 1    | 0    | 1    |
| 0    | 1    | 1   | 1    | 0    | 1    | 0    |
| 1    | 0    | 0   | 1    | 0    | 1    | 0    |
| 1    | 0    | 1   | 1    | 1    | 1    | 1    |
| 1    | 1    | 0   | 1    | 1    | 1    | 1    |
| 1    | 1    | 1   | 0    | 0    | 0    | 0    | 

$Z0=\bar{S0}X+S0\bar{X}$

$Z1=\bar{S1}S0X+S1\bar{S0}+S1S0\bar{X}$

```Verilog
module statouscita(output [1:0]z, input [1:0]s, input x);
    assign z[0] = (~s[0] & x) | (s[0] & ~x);
    assign z[1] = (~s1 & s[0] & x) | (s[1] & ~s[0]) | (s[1] & s[0] & ~x)
endmodule
```