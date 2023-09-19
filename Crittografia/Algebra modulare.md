## Valore modulare

Il valore modulare $k=N \mod m$ coincide con il reste della divisione intera tra $N$ e $m$.

Dati due interi, $a,b≥0$ e $n≥0$, $a$ è congruo a $b$ modulo $n$:
$a≡b \mod  n$
Se e solo se esiste un intero $k$ tale che $a=kb+n$

Proprietà:
- $(a+b) \mod m=(a \mod m + b \mod m) \mod m$
- $(a-b) \mod m=(a \mod m - b \mod m) \mod m$
- $(a×b) \mod m=(a \mod m × b \mod m) \mod m$
- $a^{r×s} \mod m=(a^r \mod m)^s \mod m$

Nell'aritmetica modulare le funzioni tendono a comportarsi in modo imprevedibile. Rende difficili li cose che sarebbero facili.
Per esempio, $2^x \mod 13=5$, trova $x$. Ci vuole la forza bruta a capire che $x=9 \mod 12$

## Algoritmo di Euclide

Numero coprimi: il loro MCD è 1.

Funzione di Euclide, ritorna l'MCD di $a$ e $b$:
```
function euclid(a, b) {
    if (b == 0) return a
    else return euclid(b, a mod b)
}
```

Costo: ogni due chiamate ricorsive, il parametro $a$ si riduce di almeno la metà. Dato che l'operazione modulo si esegue in tempo $O(\log_2 a✕\log_2 b$), nel peggior caso $O(\log_2^3(a))$.

## Generazione sequenza casuale

Cos'è esattamente una sequenza casuale?

Idea: una sequenza binaria $h$ è casuale se NON ammette un algoritmo di generazione la cui rappresentazione binaria sia più corta di $h$.
Per esempio, un algoritmo che genera soltanto $1$ è più corto di una lunga sequenza di $1$, quindi una sequenza di soli $1$ non è una sequenza casuale.

**Complessità di Kolmogorov**: la lunghezza del più breve programma informatico (in un dato linguaggio di programmazione) che produca l'oggetto come output

Sistemi di calcolo (ragionevoli): sono un'infinità numerabile $s_1,s_2,...,s_i,...$
$k_{s_i}(h)=\min\{|p|:s_i(p)=h\}$

$p$: programma per $s_i$
$s_i(p)=h$ (output di $p$)

$k_{s_i}(h)=|h|+c_i$
$c_i$ è una costante che rappresenta la lunghezza della parte di programma che TODO