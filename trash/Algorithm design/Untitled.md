### Karp-Rabin fingerprint

How to quickly compare files in a repository: **hasing**
How to check viruses in files

Idea: without loss of generality, $S=01110110010111…$
	$n=|s|\quad S→\text{number }N_{S}[0…2^n-1]$
	$n=|s'|\quad S→\text{number }N_{S'}[0…2^n-1]$

We want to check if $S=S'$
- Pay $O(N)$ time once to get a fingerprint
	$F(S)=N_S\%p$
	$F(S)=N_{S'}\%p$
As in hashing, we reduced comparison
from $N_S,N_{S'}∈[0..2^n-1]$ to $F(S), F(S')∈[0..p-1]$

We compare $F(S), F(S')$ in O(1) time.

Rule of the games
- Fix a range $[2..τ]$ before starting, where $τ$ is chosen according the input size
- Choose a prime $p∈[2..τ]$ *uniformly at random*
- Use $F(x)=x\%p$ as fingerprint

$k_1=N_S\quad k_2=N_{S'}$
$k_1≠k_2\text{ but } k_1\%p=k_2\%p$
	**ERROR**: $S≠S'\text{ but }F(S)=F(S')\text{ unavoidable}$

>[!info]
>Prime $p$ is **bad** for $k_1≠k_2$ if $k_1\%p=k_2\%p$

$Pr(\text{ERROR})=Pr(k_1)≠k_2∧(k_1\%p=k_2\%p)=\frac{\#\text{BAD primes}}{τ/\ln τ}\leq \frac{n}{τ/\ln τ}$

Probability space is given by *all* primes in $[2..τ]$, the number of which is $\frac{τ}{\ln τ}$

Recall that $k_1,k_2∈[0..2^n]$

>[!info]
>$\#\text{BAD primes }$dividing $k_1-k_2$ is $\leq n$

$k_1\%p=k_2\%p\iff (k_1-k_2)\%p=0$
$p \text{ bad prime}\iff p\text{ divides }D=|k_1-k_2|$
$k_1,k_2∈[0..2^n-1]⇒D∈[0..2^n-1]$

Factorization of $D$ into primes
$D=p_1^{e_1}⋅p_2^{e_2} ... p_2^{e_r}$

$r?→ r<n\text{ as }p_i \geq 2$
$r \geq n⇒D \geq2^n$, which is impossible

$\#\text{BAD primes for }D \leq r < n$

##### The final touch

>[!note]
>#WHP means "With High Probability", which is $\leq \frac{1}{\text{poly}(n)}$

In our case, $Pr(\text{error})\leq \frac{n}{τ/\ln τ}\leq \frac{1}{n^c}$ with constant $c>1$

$( n^{c+1}\leq \frac{τ}{\ln τ} \leq τ) ⇒ \text{fix }τ=n^{c+1}$

### String matching
