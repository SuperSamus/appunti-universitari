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

- **GDB**/**LLDB** permettono di analizzare il programma passo per pass
	- È necessario compilare il programma con il flag `-g` (su `gcc`/`clang`) in modo da avere i simboli di debug nel programma
	- Si può impostare *breakpoint* sulle righe di codice e *watchpoint* per le variabili
- **Valgrind** permette di analizzare la memoria allocata e localizzare memory leak
