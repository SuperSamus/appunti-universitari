# Numerali di Church

Codifica che consente ai numeri $n \in \mathbb{N}$ e alle loro operazioni di essere rappresentati con il [[λ-calcolo]]: $\mathbb{N}\longrightarrow\Lambda$

Ad ogni $n \in \mathbb{N}$ associo un termine $\overline{n}= \lambda f.\lambda x.f^n(x)$

- $f^0x = x$
- $f^nx = f(f^{n-1})$

Esempi:

- $\overline{0} = \lambda f.\lambda x.x$
- $\overline{1} = \lambda f.\lambda x.fx$;
- $\overline{2} = \lambda f.\lambda x.f(fx)$;
- $\overline{n}=\lambda f.\lambda x. f^nx$

Generica procedura $F: \mathbb{N}^k\longrightarrow\mathbb{N}$ che itera un numero di volte una funzione: $t_Fc_{n_1}…c_{n_k}\longrightarrow_\beta c_F(n_1…n_k)$.

## Operazioni

$\overline{SUCC} = \lambda n.\lambda f.\lambda x.f(nfx)$
	- $\overline{SUCC} \: \overline{n} \rightarrow_\beta \overline{n+1}$
- $\overline{ADD}=\lambda n. \lambda m. \lambda f. \lambda y. nf(mfx)$