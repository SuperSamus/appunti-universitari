# α-conversione

Forma di equivalenza del [[λ-calcolo]].

Formalmente, la relazione $=_\alpha \subseteq \Lambda \times \lambda$

$$
\frac{}{\lambda x.t =_\alpha \lambda y.t[y/x]} \quad (x \not \in FV(t))
$$

$$
\frac{}{t=_\alpha t} \text{ riflessiva} \quad \frac{t=_\alpha s}{s=_\alpha t} \text{ simmetrica} \quad \frac{t=_\alpha s \quad s=_\alpha u}{t=_\alpha u} \text{ transitiva}
$$

$$
\frac{t=_\alpha t' \quad s=_\alpha s'}{ts=_\alpha t's'} \quad \frac{t=_\alpha s}{\lambda x.t=_\alpha \lambda x.s}
$$

## Esempi

- `function succ(x) {x+1}` $=_\alpha$ `function succ(y) {y+1}`
- $\lim\limits_{x \to +\infty} e^{-x}=_\alpha \lim\limits_{y \to +\infty} e^{-y}$
- $\lambda xy.x(xy)=_\alpha \lambda ab.a(ab)$
	- $\lambda y.x(xy) =_\alpha \lambda b.x(xb)$
	- $\Rightarrow \lambda x.\lambda y.x(xy)=_\alpha \lambda x.\lambda b.x(xb) =_\alpha \lambda a.\lambda b.a(ab)$

## Lemma

$$
\frac{t =_\alpha t' \quad s=_\alpha s'}{t[s/x]=_\alpha t'[s'/x]}
$$

## NB

Ogni volta che definiamo un'operazione sul λ-calcolo (come sostituzione, ottimizzazione…), bisogno dimostrare che l'operazione è invariante per l'α-equivalenza (non dipende dalla scelta dei nomi dei parametri formali.)

$F: \Lambda^n \rightarrow \Lambda$

$t_1=_\alpha s_1,…, t_n =_\alpha s_n \Rightarrow F(t_1,…,t_n)=_\alpha F(s_1,…,s_n)$