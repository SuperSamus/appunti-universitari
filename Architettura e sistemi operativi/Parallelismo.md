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

