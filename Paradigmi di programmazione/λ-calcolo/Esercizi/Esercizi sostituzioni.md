# Esercizi [[sostituzioni]]

- $(\lambda y.x)[y/x]=(\lambda z.x[z/y])[y/x]=(\lambda z.x)[y/x]=\lambda z.y$
- $(\lambda y.x (\lambda w.vwx))[uv/x]=\lambda y.x[uv/x](\lambda w.vwx)[uv/x]=\lambda y.uv(\lambda w.(vwx)[uv/x]))=\lambda y.uv(\lambda w.vwuv)$
- $(\lambda y.x (\lambda x.x))[\lambda y.xy/x]=\lambda y.x[\lambda y.xy/x](\lambda x.x)[\lambda y.xy/x]=\lambda y.\lambda y.xy(\lambda x.x)$
- $(\lambda x.zy)[uv/x]=\lambda x.zy$