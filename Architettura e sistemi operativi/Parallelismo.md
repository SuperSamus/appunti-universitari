# Parallelismo

Se bisogna fare tre operazioni che richiedono una certa quantità di tempo ciascuno:
```
|-----|---|----|
```

**Parallelismo spaziale**: sarebbe più veloce poterle fare contemporaneamente:
```
|-----|
|---|
|----|
```

**Parallelismo temporale**: se non si può fare queste operazioni contemporaneamente, si può fare su entità diverse (immagina di preparare una torta, che ha bisogno di forno e poi altri operazioni, ma si ha un solo forno. Stile catena di montaggio):
```
 Forno
|-----|---|----|
       Forno
      |-----|---|----|
```

Il parallelismo spesso richiede risorse extra (*overhead*) rispetto alla teoria:
- Il tempo di startup (per esempio, si distribuisce il lavoro ai vari worker)
- Il tempo di raccolta (per esempio, dopo una somma fatta in parallelo, bisogna sommare le varie parti finali)

Speedup: $sp(nw)=\cfrac{T_{sec}}{T_{par(nw)}}$ ($nw$ è il numero di workers)

## Pipeline processore

TODO: rivedere fine 21 ottobre
%%
```
   tf=1  td=2  te=3  twb=2
--> F --> D --> E --> WB -->
```

$L=t_f+t_d+t_e+t_{wb}$

$T_{spaziale}=\max\{t_f,t_d,t_e,t_{wb}\}$

$sp(nw)=4⇔nw≥4$
%%