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
How to solve the I/O problem? Let's make permutation a sorting problem.

1. Scan $S→<A,1><B,2><C,3><D,4>$
2. Scan $π→<3,1><1,2><2,3><4,4>$ ($<\text{source,destination}>$)
3. Sort $π$ by the source $→<1,2><2,3><3,1><4,4>$
4. Scan of $π∧S→<A,2><B,3><C,1><D,4>$ (parallel scan)
5. Sort by destination $→<C,1><A,2><B,3><D,4>$
6. Scan $→CABD$

Explanation of Sort I/O, in multi-way mergesort:
- $\frac{n}{B}$: Scan items
- $\log_{\frac{M}{B}}\frac{n}{M}$: Phases passes
($\frac{n}{M}$ is sometimes $\frac{n}{B}$ instead)