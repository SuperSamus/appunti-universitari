# Automi

- Automa di Mealy
	- $z=f_z(s,x)$
	- $s'=f_s(s,x)$
- Automa di Moore
	- $z=f_z(s)$
	- $s'=f_s(s,x)$

Entrambi gli automi hanno bisogno di un registro per memorizzare lo stato.

Vediamoli per riconoscere `aba` (alfabeto $\{a,b,c\}$) , in una stringa (come `abcabbaba`).

## Mealy

```mermaid
flowchart LR
s1 -- b/0 --> s1
s1 -- c/0 --> s1
s1(((s1))) -- a/0 --> s2((s2)) -- c/0 --> s1
s2 -- a/0 --> s2
s2 -- b/0 --> s3((s3))
s3 -- a/1 --> s1
s3 -- b,c/0 --> s1
```

```mermaid
flowchart LR
a -- x --> fs' & fz
fs' -- s2 --> reg -- s1 --> fs' & fz
fz -- 0 --> z
```

Con il carattere ($\{a,b,c\}$) rappresentato dai bit $x_1x_0$, lo stato corrente da $b_1b_0$, il nuovo stato da $b_1'b_0'$, e il valore di riporto (quello a destra dello `/`) con $z$:

| $b_1b_0$ | $x_1x_0$ | $b_1'b_0'$ |
| -------- | -------- | ---------- |
| 00       | 00       | 01         |
| 00       | 01       | 00         |
| 00       | 10       | 00         |
| 01       | 00       | 01         |
| 01       | 01       | 10         |
| 01       | 10       | 00         |
| 10       | 00       | 00         |
| 10       | 01       | 00         |
| 10       | 10       | 00         |

$b_1'=\bar{b_1}b_0\bar{x_1}x_0$

$b_0'=\bar{b_1}\bar{b_0}\bar{x_1}\bar{x_0}+\bar{b_1}b_0\bar{x_1}\bar{x_0}$


$f_z$

| $b_1b_0$ | $x_1x_0$ | $z$ |
| -------- | -------- | --- |
| 10       | 00       | 1   |

$z=b_1\bar{b_0}\bar{x_1}\bar{x_0}$


## Moore

```mermaid
flowchart LR
s1 -- b --> s1
s1 -- c --> s1
s1(((s1/0))) -- a --> s2((s2/0)) -- c --> s1
s2 -- a --> s2
s2 -- b --> s3((s3/0))
s3 -- b,c --> s1
s3 -- a --> s4((s4/1)) -- a --> s2
s4 -- b,c --> s1
```

$z=b_1b_0$

| $b_1b_0$ | $x_1x_0$ | $b_1'b_0'$ |
| -------- | -------- | ---------- |
| 00       | 00       | 01         |
| 00       | 01       | 00         |
| 00       | 10       | 00         |
| 01       | 00       | 01         |
| 01       | 01       | 10         |
| 01       | 10       | 00         |
| 10       | 00       | 11         |
| 10       | 01       | 00         |
| 10       | 10       | 00         |
| 11       | 00       | 01         |
| 11       | 01       | 00         |
| 11       | 10       | 00         |

$b_1'=\bar{b_1}b_0\bar{x_1}x_0+b_1\bar{b_0}\bar{x_1}\bar{x_0}$

$b_0'=\bar{x_1}\bar{x_0}$

TODO: Riguardare seconda parte

## Rete che calcola parità di una sequenza di bit

input: $011010111101000$
z_:      $101100101001111$

Mealy:

```mermaid
flowchart LR
si(((si))) -- 1/0 --> sol((sol)) -- 1/1 --> si
si -- 0/1 --> si
sol -- 0/0 --> sol
```

Moore:

```mermaid
flowchart LR
si(((si/1))) -- 1 --> sol((sol/0)) -- 1 --> si
si -- 0 --> si
sol -- 0 --> sol
```

1. \# bit del registro di stato: 1
2. Tabella verità 

Mealy:

| s   | x   | s'  |
| --- | --- | --- |
| 0   | 0   | 0   |
| 0   | 1   | 1   |
| 1   | 0   | 1   |
| 1   | 1   | 0   | 

| s   | x   | z   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 0   | 1   | 0   |
| 1   | 0   | 0   |
| 1   | 1   | 1   |