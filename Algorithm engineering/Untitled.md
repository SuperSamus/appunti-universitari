$S[1,n]$
$π[1,n]=\text{permutation of \{1,2,...,n\}}$

Example:
$S=[A,B,C,D]$
$π=[3,1,2,4]$
$S'=[C,A,B,D]$

```python
def permutation(s, π):
	for i in range(n):
		s1[i]=s[π[i]]
	s = s1
```

|      | Permuting   | Sorting                                    |
| ---- | ----------- | ------------------------------------------ |
| RAM  | $n$         | $n\log n$                                  |
| Disk | $n$ (worst) | $\frac{n}{B}\log_{\frac{M}{B}}\frac{n}{M}$ |
(See [[Intro#External memory model]])
How to solve the I/O problem? Let's make permutation a sorting problem.

1. Scan $S→<A,1><B,2><C,3><D,4>$
2. Scan $π→<3,1><1,2><2,3><4,4>$ ($<\text{source,destination}>$)
3. Sort $π$ by the source $→<1,2><2,3><3,1><4,4>$
4. Scan of $π∧S→<A,2><B,3><C,1><D,4>$ (parallel scan)
5. Sort by destination $→<C,1><A,2><B,3><D,4>$
6. Scan $→CABD$

Explanation of Sort I/O, for k-way mergesort:
- $\frac{n}{B}$: Scan items
- $\log_k\frac{n}{M}$: Phases passes
	- The optimal $k$ is $\frac{M}{B}$ (-1, since mergesort isn't in-place)
	- To achieve $\frac{n}{M}$ instead of $\frac{n}{B}$, start by:
		- Fetch as much as it fits on memory ($\frac{M}{B}$ reads)
		- Sort "normally"
		- Write back to disk ($\frac{M}{B}$ writes)
		- Repeat until all of $n$ is sorted in each "block of memory"
(Regular mergesort is $\frac{n}{B}\log_2 \frac{n}{B}$)

$\text{Permuting}=\text{Sorting}⟺\frac{n}{B}\log_{\frac{M}{B}}\frac{n}{M}≤n⟺B≥\log_{\frac{M}{B}}\frac{n}{M}$
