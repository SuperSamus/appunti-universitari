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
=AB*(c)
$$