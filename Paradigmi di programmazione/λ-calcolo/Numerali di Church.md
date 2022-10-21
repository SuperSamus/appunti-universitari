# Numerali di Church

Codifica che consente ai numeri $n ∈ ℕ$ e alle loro operazioni di essere rappresentati con il [[λ-calcolo]]: $ℕ\longrightarrowΛ$

Ad ogni $n ∈ ℕ$ associo un termine $\underline{n}= λf.λx.f^n(x)$

- $f^0x = x$
- $f^{n+1}x = f(f^n)$

Esempi:

- $\underline{0} = λf.λx.x$
- $\underline{1} = λf.λx.fx$;
- $\underline{2} = λf.λx.f(fx)$;
- $\underline{n} = λf.λx.f^nx=λf.λx.f^nx$

Generica procedura $F: ℕ^k\longrightarrowℕ$ che itera un numero di volte una funzione: $t_Fc_{n_1}…c_{n_k}\longrightarrow_β c_F(n_1…n_k)$.

## Operazioni

Per implementare le operazioni, bisogna dimostrare le proprietà che hanno. Per esempio:
- $ADD(\underline{n},\underline{m})→_β^*\underline{n+m}$
- $ADD(\underline{n},\underline{m})→_β^*ADD(\underline{m},\underline{n})$
	- Questo è difficile da dimostrare, ma non ci interessa molto dato che vogliamo solo programmare.

### SUCC

$\underline{SUCC} = λn.λf.λx.f(nfx)$

 $$
\underline{SUCC} \: \underline{n} \\
=(λn.λf.λx.f(nfx))\underline{n} \\
→_β λf.λx.f(\underline{n}fx) \\
→_β λf.λx.f(f^nx) \\
=\underline{n+1}
$$

$∀n. \underline{n}fx →_β f^nx$

$\underline{n}fx=(λf.λx.f^nx)fx$

#### Esempi

* $\underline{SUCC} \: \underline{0} →_β λf.λx.f(\underline{0}fx) = λf.λx.f((λf.λx.x)fx) →_β λf.λx.fx$
* $\underline{SUCC} \: \underline{1} →_β λf.λx.f(\underline{1}fx) = λf.λx.f((λf.λx.fx)fx) →_β λf.λx.f(fx)$
* $\underline{SUCC} \: \underline{2} →_β λf.λx.f(\underline{1}fx) = λf.λx.f((λf.λx.f(fx))fx) →_β λf.λx.f(f(fx))$

### ADD

$\underline{ADD}=λn.λm.λf.λx.nf(mfx)$

$\underline{ADD} \:\underline{n} \: \underline{m} →_β f^n(f^mx)=f^{n+m}=\underline{n+m}$

#### Esempi

$$
\underline{ADD} \: \underline{2} \: \underline{3} \\
= (λn.λm.λf.λx.(nf(mfx)))(λf.λx.f(fx))(λf.λx.f(f(fx))) \\
→_β (λm.λf.λx.(λf.λx.f(fx))f(mfx))(λf.λx.f(f(fx))) \\
→_β (λf.λx.(λf.λx.f(fx))f(λf.λx.f(f(fx)))fx) \\
→_β (λf.λx.(λf.λx.f(fx))f(f(f(fx)))) \\
→_β (λf.λx.(λx.f(fx))(f(f(fx)))) \\
→_β (λf.λx.f(f(f(f(fx)))))
$$

### MULT

$\underline{MULT} = λn.λm.λf.n(mf)$

## Funzione di codifica

Esiste sempre una funzione $\underline{F}$ che codifica una funzione "normale" nel λ-calcolo.

$F: ℕ^k ⇀ ℕ$

$∃ \underline{F} ∈ Λ.∀n_1,…,n_k.F(n_1,…,n_k)=m \quad \underline{F} \: \underline{n_1}…\underline{n_k} →_β^* \underline{m}$

## Liste

Nel linguaggio $e::=...|nil|e::e|...$, una lista si rappresenta per esempio come $1::(2::(3::nil))$.

$a := [1, 2, 3] = λcn.c 1 (c 2 (c 3 n))$

Le operazioni base $\underline{nil}$ (costruisci una lista vuota) e $\underline{cons}$ (aggiungi un valore a inizio lista) sono definite come:
- $\underline{nil} ≜λx.λy.y$
- $\underline{cons} ≜λh.λt.λx.λy.ht$

Altre funzioni:
- $foldr⊕[x_1...x_n]z → (x_1⊕(x_2⊕...(x_n⊕z)))$
- $foldl⊕[x_1...x_n]A → (((A⊕x_1)⊕x_2)...x_n)$
