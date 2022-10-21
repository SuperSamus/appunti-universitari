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

Il parallelismo spesso richiede risorse extra (*overhead*) per coordinarsi.

## Pipeline processore

```
    tf    td    te    twb
--> F --> D --> E --> WB -->
```

$L=t_f+t_d+t_e+t_{wb}$

$T_S=\max\{t_f,t_d,t_e,t_{wb}\}$

Speedup $sp(nw)=4⇔nw≥4$