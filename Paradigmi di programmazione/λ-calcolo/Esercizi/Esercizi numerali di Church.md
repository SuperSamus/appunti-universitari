# Esercizi [[numerali di Church]]

β-ridurre:
* $\overline{SUCC} \: \overline{0} \rightarrow_\beta \lambda f. \lambda x. f(\overline{0}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.x)fx) \rightarrow_\beta \lambda f.\lambda x. fx$
* $\overline{SUCC} \: \overline{1} \rightarrow_\beta \lambda f. \lambda x. f(\overline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.fx)fx) \rightarrow_\beta \lambda f.\lambda x. f(fx)$
* $\overline{SUCC} \: \overline{2} \rightarrow_\beta \lambda f. \lambda x. f(\overline{1}fx) = \lambda f. \lambda x. f((\lambda f.\lambda x.f(fx))fx) \rightarrow_\beta \lambda f.\lambda x. f(f(fx))$

Calcolare $\overline{ADD} \: \overline{2} \: \overline{3}$
$$
= (\lambda n. \lambda m. \lambda f. \lambda y. (nf(mfx)))(\lambda f.\lambda x.f(fx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda m. \lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(mfx))(\lambda f.\lambda x.f(f(fx))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(\lambda f.\lambda x.f(f(fx)))fx) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda f.\lambda x.f(fx))f(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. (\lambda x.f(fx))(f(f(fx)))) \\
\rightarrow_\beta (\lambda f. \lambda y. f(f(f(f(fx)))))
$$
