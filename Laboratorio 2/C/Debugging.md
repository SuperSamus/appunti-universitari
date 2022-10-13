# Debugging

`printf` non è la migliore idea per fare debugging: la stringa viene salvata in un buffer, che verrà stampata solo dopo. Un errore può prevenire che venga stampata, perché è rimasta nel buffer. `fprintf` non ha questo "difetto".

## Assert

```c
#define NDEBUG // Per disabilitare gli assert
#include <assert.h>

int main() {
  assert(1 > 0); // Il programma continua
  assert(-1 > 0) // Segmentation fault
}
```

## Debugger

- GDB/**LLDB** permettono di analizzare il programma passo per pass
- **Valgrind** permette di analizzare la memoria allocata e localizzare memory leak

Non si può fare il debugging su librerie precompilate.