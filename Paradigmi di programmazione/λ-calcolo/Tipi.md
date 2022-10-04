## Strategie di valutazione

$(\lambda x.x^2+2x+3)(\underline{2+3}))$

- Chiamata per nome (CbN): rimpiazza $x$ con $2+3$
	- $\rightarrow_\beta t[s/x]$
- Chiamata per valore (CbV): valuta $2+3$, e rimpiazza $x$ con il risultato
	- $\rightarrow^\star(\lambda x.t)v \rightarrow_\beta t[v/x]$


$KI\Omega \stackrel{\Delta}{=} (\lambda x.\lambda y.x)I\Omega$

- CbV: $KI\Omega$
- CbN: $(\lambda y.I)\Omega$
	- CbV: ()