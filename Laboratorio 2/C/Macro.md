# Macro

- Costruiti con direttiva preprocessore `#define`
	- `#define N 100`
		- Definisce una macro con nome `N` e valore `100`

```c
#include <stdio.h>

#define MAX(A, B)       \
  if (A > B)            \
    printf("%d", A);    \
  else                  \
    printf("%d", B);

int main() {
  int x, y;
  scanf("%d %d", &x, &y);

  MAX(x, y)
}
```