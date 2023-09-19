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