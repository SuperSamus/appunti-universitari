La *norma vettoriale* per un vettore $x∈ℝ^n$ ha le seguenti proprietà
- $||x||≥0$, e $||x||=0⇔x=0$
- $∀α∈ℝ\:||αx||=|a|\:||x||$
- $||x+y||≤||x||+||y||$ (*disuguaglianza triangolare*)

Esempi di norme vettoriali:
- Norma 1: $∑\limits_{i=1}^n|x_i|$
- Norma 2: $\sqrt{x^Tx}=\sqrt{∑\limits_{i=1}^nx_i^2}$
- Norma ∞: $\max_i |x_i|$
- Norma $p$: $\sqrt[p]{∑\limits_{i=1}^n|x_i|^p}$


La *norma matriciale* per una matrice $A∈ℝ^{n×n}$ ha le stesse proprietà, più:
- $||AB||≤||A||\:||B||$

Esempi di norme matriciali:
- Norma 1: $\max_j ∑\limits_{i=1}^n|a_{ij}|$
- Norma 2: $ρ(\sqrt{A^HA})$
- Norma ∞: $\max_i ∑\limits_{j=1}^n|a_{ij}|$

Una norma vettoriale è detta *compatibile* con una norma matriciale se:
$||Ax||_v≤||A||_m||x||_v$
 per ogni $x∈ℝ^n$

>[!info]
>Dato che $||λx||_v=|λ|\:||x||_v=||Ax||_m$, questo implica che $||λ||_v≤||A||_m$

Se $\max\limits_{||x||_v=1}||Ax||_v=||A||_m$, allora la norma è detta *indotta*.
