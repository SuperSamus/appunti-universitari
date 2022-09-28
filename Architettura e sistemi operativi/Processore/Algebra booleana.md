# Algebra booleana

Assiomi:
- NOT
	- $\overline{0}=1$
	- $\overline{1}=0$
- AND
	- $0*0=0$
	- $1*1=1$
	- $1*0=0$
	- $0*1=0$
- OR
	- $0+0=0$
	- $1+1=1$
	- $1+0=1$
	- $0+1=1$

## Teoremi

$ABC \: var \in \{0,1\}$

|     | Identità | Elemento nullo | Idempotenza | Complementi        | Commutativa | Associativa       |
|:---:| -------- | -------------- | ----------- | ------------------ | ----------- | ----------------- |
| AND | $A*1=A$  | $A*0=0$        | $A*A=A$     | $A*\overline{A}=0$ | $A*B=B*A$   | $(A*B)*C=A*(B*C)$ |
| OR  | $A+1=1$  | $A+0=A$        | $A+A=A$     | $A+\overline{A}=1$ | $A+B=B+A$   | $(A+B)+C=A+(B+C)$ |

- Distributiva: $A*(B+C)=A*B+A*C$ |
- Involuzioni: $\overline{\overline{A}}=A$
- De Morgan: $\overline{A*B}=\overline{A}+\overline{B}$

# TODO

## Ottimizzazione

Funzione obiettivo: combinazione a piacere tra:
- \# porte
- Velocità
- Design time
- Costo (silicio)
- Consumo (silicio)

### Semplificazione di espressioni booleane

$$
ABC+AB \overline{C}+\overline{A}B \\
=AB*(C+\overline{C})+\overline{A}B \\
=AB+\overline{A}B \\
=(A+\overline{A})B \\
=B
$$

# TODO: sistema questa tabella

| $ABC$ | $AB\overline{C}$ | $+$ | B   |
| ----- | ---------------- | --- | --- |
| 000   | 000              | 0   | 0   |
| 001   | 000              | 0   | 0   |
| 010   | 001              | 1   | 1   |
| 011   | 001              | 1   | 1   |
| 100   | 000              | 0   | 0   |
| 101   | 000              | 0   | 0   |
| 110   | 010              | 1   | 1   |
| 111   | 100              | 1   | 1   |

$$
ABC+A\overline{B}\:\overline{C}+AB\overline{C} \\
=ABC+AB\overline{C}+A\overline{B}\:\overline{C}+AB\overline{C} \\
=AB(C+\overline{C})+A\overline{C}(\overline{B}+B) \\
=AB+A\overline{C} \\
=A(B+\overline{C})
$$
$$
A\overline{B}\:\overline{C}+AB\overline{C}+\overline{A}BC+ABC \\
=A\overline{C}(\overline{B}+B)+(\overline{A}+A)BC \\
=A\overline{C}+BC
$$

| ABC | z   |
| --- | --- |
| 1-0 | 1   |
| -11 | 1   |
| 1-0 | 0   |
| -01 | 0   |

Questo è un multiplexer, visto su [[Porte logiche#Altro esempio]].

# TODO: l'esempio che ha fatto dopo

NAND

| AB  | z   |
| --- | --- |
| 00  | 1   |
| 01  | 1   |
| 10  | 1   |
| 11  | 0   |

### NOT

```mermaid
flowchart LR
A -- 1 --> B[NAND] & B
B -- 0 --> z
```

### AND

```mermaid
flowchart LR
A & B --> N1[NAND]
N1 & N1 --> N2[NAND]
```

### OR (De Morgan)

```mermaid
flowchart LR
A & A --> N1[NAND] --> N3[NAND]
B & B --> N2[NAND] --> N3
```

## Mappe di Karnaugh

Può essere 2, 3 o 4 variabili

### 2 variabili
| AB  | z   |
| --- | --- |
| 00  | 1   |
| 01  | 1   |
| 10  | 1   |
| 11  | 0   |

| A\\B | 0   | 1   |
| ---- | --- | --- |
| 0    | 1   | 1   |
| 1    | 1   | 0   |

### 3 variabili
| A\\BC | 00  | 01  | 11  | 10  |
| ----- | --- | --- | --- | --- |
| 0     |     |     |     |     |
| 1     |     |     |     |     |

### 4 variabili

# TODO: sigh...
| AB\\CD | 00                                         | 01               | 11  | 10               |
| ------ | ------------------------------------------ | ---------------- | --- | ---------------- |
| 00     | $\overline{B}\:\overline{C}\:\overline{D}$ |                  |     |                  |
| 01     | $AB\overline{D}$                           | $AB\overline{D}$ |     |                  |
| 11     |                                            |                  |     | $AC\overline{D}$ |
| 10     | $\overline{B}\:\overline{C}\:\overline{D}$ |                  |     | $AC\overline{D}$ |