# Funzioni

- **Astrazione**: implementano una certa funzionalità per essere riutilizzata.
- Il passaggio viene sempre fatto per *valore* (copia)
- Per cambiare il valore degli argomenti si usano i [[puntatori]]


## Sintassi

- **Dichiarazione**
    - Se manca: **linker error**
    - Spesso si fa in file separati, gli **header** (`.h`)
- **Definizione**
    - Se manca: **compiler error**

## Parametri riga di comando

```c
int main(int argc, char* argv[])
```

- `argv[0]` nome del programma

## Numeri di parametri variabile

- Numero parametri variabile con **ellipsis** (`...`): `void f(char x, ...)`
    - È necessario almeno un parametro "normale"
    - Per accedere ai parametri si usano macro definiti in `stdarg.h`
        - `va_list` (tipo)
        - `va_start` (funzione)
        - `va_arg` (funzione)
        - `va end` (funzione)

```c
#include <stdarg.h>
#include <stdio.h>

double sum(int n, ...) {
  double sum = 0;
  va_list args;
  va_start(args, n);

  for (int i = 0; i < n; ++i) {
    sum += va_arg(args, double);
  }

  va_end(args);
  return sum;
}

int main() {
  printf("%f %f %f", sum(2, 7., 3.), sum(7, 1., 2., 3., 4., 5., 6., 7.), sum(0));
}
```
