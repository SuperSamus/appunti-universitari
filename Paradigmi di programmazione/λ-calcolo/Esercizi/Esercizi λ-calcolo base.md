# Esercizi [[λ-calcolo]] base

Determinare quali delle seguenti espressioni sono λ-termini:

- $\lambda$ NO
- $(\lambda x)$ NO
- $\lambda x.y$ SI
- $xxxx$ NO
- $\lambda (xy).x$ NO
- $x$ SI
- $y$ SI
- $xx$ SI
- $(\lambda x.(x(\lambda y)))$ NO

Inserire le parentesi mancanti

- $xyz(yx) \rightarrow ((((x)y)z)(yx))$
- $\lambda xyz.x(yz) \rightarrow (\lambda x. \lambda y. \lambda z.x(yz))$
- $ux(yz)(\lambda v.vy) \rightarrow ((((u)x)y)z)(\lambda v.vy))$
- $\lambda xyz.xz(yz) \rightarrow (\lambda x. \lambda y. \lambda z.(((x)z)y)z)$

Trova le FV:

- $FV(xv(\lambda yz.yv)w)=\{x,v,v,w\}$
