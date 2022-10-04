## Strategie di valutazione

$(\lambda x.x^2+2x+3)(\underline{2+3}))$

- Chiamata per nome (CbN): rimpiazza $x$ con $2+3$
	- $\rightarrow_\beta t[s/x]$
- Chiamata per valore (CbV): valuta $2+3$, e rimpiazza $x$ con il risultato
	- $\rightarrow^\star(\lambda x.t)v \rightarrow_\beta t[v/x]$

##

Ci sono $t\downarrow_{CbN}$ ($t$ termina) e $t\uparrow_{CbV}$ ($t$ non termina).
- $KI\Omega \stackrel{\Delta}{=} (\lambda x.\lambda y.x)I\Omega$
	- CbV: $KI\Omega$
	- CbN: $(\lambda y.I)\Omega$
		- CbV: $(\lambda y.I)\Omega$
		- CbN: $I$

Non vale viceversa. Teorema: se $t\rightarrow_\beta^\star s \not \rightarrow$ allora $t \xrightarrow{CbN}_\beta^\star s$

CbV però è più efficiente.

Call-by-Need: valuta qualcosa solo se serve. Detto anche lazy. Utile per gli invinitesimi.

Hask