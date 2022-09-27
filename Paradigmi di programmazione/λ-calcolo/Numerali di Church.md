# Numerali di Church

Codifica che consente ai numeri $n \in \mathbb{N}$ e alle loro operazioni di essere rappresentati con il [[λ-calcolo]]: $\mathbb{N}\longrightarrow\Lambda$

Ad ogni $n \in \mathbb{N}$ associo un termine $c_n= \lambda f.\lambda x.f^n(x)$

- $f^0x = x$
- $f^nx = f(f^{n-1})$

Esempi:

- $c_0 = \lambda f.\lambda x.x$
- $c_1 = \lambda f.\lambda x.fx$;
- $c_2 = \lambda f.\lambda x.f(fx)$;

Generica procedura $F: \mathbb{N}^k\longrightarrow\mathbb{N}$ che itera un numero di volte una funzione: $t_Fc_{n_1}…c_{n_k}\longrightarrow_\beta c_F(n_1…n_k)$.

## Esercizi

[[Esercizi sostituzioni]]