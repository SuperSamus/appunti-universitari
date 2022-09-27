# Array

- `int a[10];`
    - Alloca sullo #stack 10 indirizzi continui
    - Memorizza in `a` l'indirizzo della prima cella
        - Le variabili come `a` sono [[puntatori]]
- Array multidimensionali: negli argomenti delle funzioni, serve specificare la dimensione di tutte le "dimensioni" (eccetto la prima)
- Array statici: allocati sullo #stack
- Array dinamici: allocati sul heap
- `a == &(a[0])`
- `&(a[1]) == (a+1)`
- `&(a[i]) == (a+i)`