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
=ABC+A\overline{B}\:\overline{C}+A\overline{B}\:\overline{C}+AB\overline{C} \\
=A(BC+\overline{B}\:)
$$