# Esercizi [[β-riduzione]]

$SUCC = \lambda n.\lambda f.\lambda x.f(nfx)$

β-ridurre:
* $SUCC \: c_0 \rightarrow_\beta \lambda f. \lambda x. f(c_0fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.x)fx) \rightarrow_\beta \lambda f.\lambda x. fx$
* $SUCC \: c_1 \rightarrow_\beta \lambda f. \lambda x. f(c_1fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.fx)fx) \rightarrow_\beta \lambda f.\lambda x. f(fx)$
* $SUCC \: c_2 \rightarrow_\beta \lambda f. \lambda x. f(c_1fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.f(fx))fx) \rightarrow_\beta \lambda f.\lambda x. f(f(fx))$

Dimostra:
- $SUCC \: c_n \rightarrow_\beta c_{n+1}$

# TODO

$ADD=\lambda n. \lambda m. \lambda f. \lambda y. nf(mfx)$

Calcolare $ADD \: c_2c_3$
$$
= (\lambda n. \lambda m. \lambda f. \lambda y. (nf(mfx)))(\lambda f.\lambda x.f(fx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda m. \lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(mfx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(\lambda f.\lambda x.f(f(fx)))fx) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda x.f(fx))(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. f(f(f(f(fx)))))
$$
