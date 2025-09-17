Traditional #algorithm:
- Finite
- Definite
- Effective
- Procedure (steps)

Solve a problem: a function $f$ For each input -> Correct output

AI is different: **heuristic programming**

Time complexity: $T(n)$, with $n$ being the *input size*
\# steps token by algorithm to implement $f$
- Worst case analysis
- Average case analysis
The graph time-per-input-size is almost-always non-decreasing

If there are two algorithms, one faster at input size $i$ where $0≤i≤n$, and the other faster where $n≤i≤+∞$, the best algorithm is one that chooses the faster algorithm depending on size.

**RAM model**: Random Access Machine <small>(not memory)</small>: there is only unbounded memory (no load-store)
- The assumptions of the model make it pretty bad. Need a better balance of assumptions with the model.

### External memory model

The CPU is connected to an external memory, connected to an unbounded storage disk

Not only you count the number of steps, but also the number of reads/writes on disk blocks, plus the memory usage
- (For simplification purposes, the various layers of CPU cache are excluded. If the data is small, the model sets the memory bound to the CPU cache size, meaning that cache misses are equivalent to disk reads.)
- **Locality of data** becomes important

Not only "given a certain input size, what's the time?", but also "given a fixed time, what input size can it manage?"
Let's say you get a machine that is $k$ times faster. How much slower is the old machine?
- $T_1(n)=n\quad n=t→n'=kt$
- $T_2(n)=n^2\quad n=\sqrt{t}→n'=\sqrt{kt}$
- $T_3(n)=2^n\quad \log_2 n=t→n'=\log_2 k+\log_2 t$

Given a random disk access, the probability of needing an I/O read if the disk is $ε$ times bigger than memory, is $p(ε)=\frac{εM}{(1+ε)M}=\frac{ε}{1+ε}$

If the cost of a disk access is $c$, the cost of a regular operation is $1$, and the ratio of memory operations is $a$, the formula of slowdown due to reads is $(1-a)·1+a[(1-p(ε))·1+p(ε)·c]≃a·p(ε)·c$

I/O bounds will use the following parameters:
- $B$: Disk block size
- $M$: Memory size