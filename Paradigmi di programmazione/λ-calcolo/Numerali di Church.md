# Numerali di Church

Codifica che consente ai numeri $n \in \mathbb{N}$ e alle loro operazioni di essere rappresentati con il [[λ-calcolo]]: $\mathbb{N}\longrightarrow\Lambda$

Ad ogni $n \in \mathbb{N}$ associo un termine $\underline{n}= \lambda f.\lambda x.f^n(x)$

- $f^0x = x$
- $f^{n+1}x = f(f^n)$

Esempi:

- $\underline{0} = \lambda f.\lambda x.x$
- $\underline{1} = \lambda f.\lambda x.fx$;
- $\underline{2} = \lambda f.\lambda x.f(fx)$;
- $\underline{n}=\lambda f.\lambda x. f^nx=\lambda f.\lambda x.f^nx$

Generica procedura $F: \mathbb{N}^k\longrightarrow\mathbb{N}$ che itera un numero di volte una funzione: $t_Fc_{n_1}…c_{n_k}\longrightarrow_\beta c_F(n_1…n_k)$.

## Operazioni

### SUCC

$\underline{SUCC} = \lambda n.\lambda f.\lambda x.f(nfx)$

 $$
\underline{SUCC} \: \underline{n} \\
=(\lambda n.\lambda f.\lambda x.f(nfx))\underline{n} \\
\rightarrow_\beta \lambda f.\lambda x.f(\underline{n}fx) \\
\rightarrow_\beta \lambda f. \lambda x.f(f^nx) \\
=\underline{n+1}
$$

$\forall n. \underline{n}fx \rightarrow_\beta f^nx$

$\underline{n}fx=(\lambda f.\lambda x.f^nx)fx$

#### Esempi

* $\underline{SUCC} \: \underline{0} \rightarrow_\beta \lambda f. \lambda x. f(\underline{0}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.x)fx) \rightarrow_\beta \lambda f.\lambda x. fx$
* $\underline{SUCC} \: \underline{1} \rightarrow_\beta \lambda f. \lambda x. f(\underline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.fx)fx) \rightarrow_\beta \lambda f.\lambda x. f(fx)$
* $\underline{SUCC} \: \underline{2} \rightarrow_\beta \lambda f. \lambda x. f(\underline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.f(fx))fx) \rightarrow_\beta \lambda f.\lambda x. f(f(fx))$

### ADD

$\underline{ADD}=\lambda n. \lambda m. \lambda f. \lambda x. nf(mfx)$

$\underline{ADD} \:\underline{n} \: \underline{m} \rightarrow_\beta f^n(f^mx)=f^{n+m}=\underline{n+m}$

#### Esempi

$$
\underline{ADD} \: \underline{2} \: \underline{3} \\
= (\lambda n. \lambda m. \lambda f. \lambda x. (nf(mfx)))(\lambda f.\lambda x.f(fx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda m. \lambda f. \lambda x. (\lambda f.\lambda x.f(fx))f(mfx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda f. \lambda x. (\lambda f.\lambda x.f(fx))f(\lambda f.\lambda x.f(f(fx)))fx) \\
\rightarrow_\beta (\lambda f. \lambda x. (\lambda f.\lambda x.f(fx))f(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda x. (\lambda x.f(fx))(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda x. f(f(f(f(fx)))))
$$

## MULT

$\underline{MULT} = λn.λm.λf.n(mf)$

## Funzione di codifica

Esiste sempre una funzione $\underline{F}$ che codifica una funzione "normale" nel λ-calcolo.

$F: \mathbb{N}^k \rightharpoonup \mathbb{N}$

$\exists \underline{F} \in \Lambda.\forall n_1,...,n_k.F(n_1,...,n_k)=m \quad \underline{F} \: \underline{n_1}...\underline{n_k} \rightarrow_\beta^\star \underline{m}$
