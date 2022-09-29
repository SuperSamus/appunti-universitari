# Algebra booleana

## Assiomi

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

## Teorema

^23603f

$ABC \: var \in \{0,1\}$

|     | Identità | Elemento nullo | Idempotenza | Complementi        | Commutativa | Associativa       |
|:---:| -------- | -------------- | ----------- | ------------------ | ----------- | ----------------- |
| AND | $A*1=A$  | $A*0=0$        | $A*A=A$     | $A*\overline{A}=0$ | $A*B=B*A$   | $(A*B)*C=A*(B*C)$ |
| OR  | $A+1=1$  | $A+0=A$        | $A+A=A$     | $A+\overline{A}=1$ | $A+B=B+A$   | $(A+B)+C=A+(B+C)$ |

- Distributiva: $A*(B+C)=A*B+A*C$ |
- Involuzioni: $\overline{\overline{A}}=A$
- De Morgan: $\overline{A*B}=\overline{A}+\overline{B}$

Sfrutteremo queste regole per ridurre il numero di [[Porte logiche]] usate. Al momento, l'espressione somma di prodotti (∀ "1" nella colonna z → Lemma AND di tanti ingressi quante sono le variabili d'input) con $k$ input ha al massimo $2^k-1$ z uguali a 1.

## Ottimizzazione

Funzione obiettivo: combinazione a piacere tra:
- \# porte
- Velocità
- Design time
- Costo (silicio)
- Consumo (silicio)

### Semplificazione di espressioni booleane

#### Esempio 1

$$
ABC+AB \overline{C}+\overline{A}B \\
=AB*(C+\overline{C})+\overline{A}B \\
=AB+\overline{A}B \\
=(A+\overline{A})B \\
=B
$$

| $A$ | $B$ | $C$ | $ABC$ | $AB\overline{C}$ | $\overline{A}B$ | $+$ | $B$ |
| --- | --- | --- | ----- | ---------------- | --------------- | --- | --- |
| 0   | 0   | 0   | 0     | 0                | 0               | 0   | 0   |
| 0   | 0   | 1   | 0     | 0                | 0               | 0   | 0   |
| 0   | 1   | 0   | 0     | 0                | 1               | 1   | 1   |
| 0   | 1   | 1   | 0     | 0                | 1               | 1   | 1   |
| 1   | 0   | 0   | 0     | 0                | 0               | 0   | 0   |
| 1   | 0   | 1   | 0     | 0                | 0               | 0   | 0   |
| 1   | 1   | 0   | 0     | 1                | 0               | 1   | 1   |
| 1   | 1   | 1   | 1     | 0                | 0               | 1   | 1   |

Da 3 AND (da 3) e 1 OR (da 3), a semplicemente il valore di $B$!

#### Esempio 2

$$
ABC+A\overline{B}\:\overline{C}+AB\overline{C} \\
=ABC+AB\overline{C}+A\overline{B}\:\overline{C}+AB\overline{C} \\
=AB(C+\overline{C})+A\overline{C}(\overline{B}+B) \\
=AB+A\overline{C} \\
=A(B+\overline{C})
$$

#### Esempio 3

$$
A\overline{B}\:\overline{C}+AB\overline{C}+\overline{A}BC+ABC \\
= A\overline{C}(\overline{B}+B)+(\overline{A}+A)BC \\
= A\overline{C}+BC
$$

| A   | B   | C   | z   |
| --- | --- | --- | --- |
| 1   | -   | 0   | 1   |
| -   | 1   | 1   | 1   |
| 0   | -   | 0   | 0   |
| -   | 0   | 1   | 0   |

$z=A\overline{C}+BC=$ Prima riga + Seconda riga

Questo è un [[Porte logiche#^b31833|multiplexer]] (con C che fa da arbitro).

## NAND

| A|B  | z   |
| --- | --- |
| 0|0  | 1   |
| 0|1  | 1   |
| 1|0  | 1   |
| 1|1  | 0   |

Permette di creare tutte le altre porte usando solo se stesso (stessa cosa per NOR). Non è il massimo dell'efficienza però:

### NOT

```mermaid
flowchart LR
A -- 1 --> B[NAND] & B
B -- 0 --> z
```

```mermaid
flowchart LR
A -- 0 --> B[NAND] & B
B -- 1 --> z
```

### AND

```mermaid
flowchart LR
A & B --> N1[NAND]
N1 & N1 --> N2[NAND]
```

### OR
Sfrutta De Morgan (Vedi [[Algebra booleana#^23603f|teoremi]])

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

# TODO: sigh…

| AB\\CD | 00                                         | 01               | 11  | 10               |
| ------ | ------------------------------------------ | ---------------- | --- | ---------------- |
| 00     | $\overline{B}\:\overline{C}\:\overline{D}$ |                  |     |                  |
| 01     | $AB\overline{D}$                           | $AB\overline{D}$ |     |                  |
| 11     |                                            |                  |     | $AC\overline{D}$ |
| 10     | $\overline{B}\:\overline{C}\:\overline{D}$ |                  |     | $AC\overline{D}$ |
