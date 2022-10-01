# Numerali di Church

Codifica che consente ai numeri $n \in \mathbb{N}$ e alle loro operazioni di essere rappresentati con il [[λ-calcolo]]: $\mathbb{N}\longrightarrow\Lambda$

Ad ogni $n \in \mathbb{N}$ associo un termine $\overline{n}= \lambda f.\lambda x.f^n(x)$

- $f^0x = x$
- $f^{n+1}x = f(f^n)$

Esempi:

- $\overline{0} = \lambda f.\lambda x.x$
- $\overline{1} = \lambda f.\lambda x.fx$;
- $\overline{2} = \lambda f.\lambda x.f(fx)$;
- $\overline{n}=\lambda f.\lambda x. f^nx=\lambda f.\lambda x.f^nx$

Generica procedura $F: \mathbb{N}^k\longrightarrow\mathbb{N}$ che itera un numero di volte una funzione: $t_Fc_{n_1}…c_{n_k}\longrightarrow_\beta c_F(n_1…n_k)$.

## Operazioni

### SUCC

$\overline{SUCC} = \lambda n.\lambda f.\lambda x.f(nfx)$

 $$
\overline{SUCC} \: \overline{n} \\
=(\lambda n.\lambda f.\lambda x.f(nfx))\overline{n} \\
\rightarrow_\beta \lambda f.\lambda x.f(\overline{n}fx) \\
\rightarrow_\beta \lambda f. \lambda x.f(f^nx) \\
=\overline{n+1}
$$

$\forall n. \overline{n}fx \rightarrow_\beta f^nx$

$\overline{n}fx=(\lambda f.\lambda x.f^nx)fx$

#### Esempi

* $\overline{SUCC} \: \overline{0} \rightarrow_\beta \lambda f. \lambda x. f(\overline{0}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.x)fx) \rightarrow_\beta \lambda f.\lambda x. fx$
* $\overline{SUCC} \: \overline{1} \rightarrow_\beta \lambda f. \lambda x. f(\overline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.fx)fx) \rightarrow_\beta \lambda f.\lambda x. f(fx)$
* $\overline{SUCC} \: \overline{2} \rightarrow_\beta \lambda f. \lambda x. f(\overline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.f(fx))fx) \rightarrow_\beta \lambda f.\lambda x. f(f(fx))$

### ADD

- $\overline{ADD}=\lambda n. \lambda m. \lambda f. \lambda y. nf(mfx)$

$\overline{ADD} \:\overline{n} \: \overline{m} \rightarrow_\beta f^n(f^mx)=f^{n+m}=\overline{n+m}$

#### Esempi

$$
\overline{ADD} \: \overline{2} \: \overline{3} \\
= (\lambda n. \lambda m. \lambda f. \lambda y. (nf(mfx)))(\lambda f.\lambda x.f(fx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda m. \lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(mfx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(\lambda f.\lambda x.f(f(fx)))fx) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda x.f(fx))(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. f(f(f(f(fx)))))
$$

## Funzione di codifica

Esiste sempre una funzione $\overline{F}$ che codifica una funzione "normale" nel λ-calcolo.

$F: \mathbb{N}^k \rightharpoonup \mathbb{N}$

$\exists \overline{F} \in \Lambda.\forall n_1,...,n_k.F(n_1,...,n_k)=m \quad \overline{F} \: \overline{n_1}...\overline{n_k} \rightarrow_\beta^\star \overline{m}$
