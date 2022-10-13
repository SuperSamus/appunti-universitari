# Stringhe

[[Array]] di caratteri, con `\0` (carattere null) alla fine.

```c
char s[]="ciao";
```
| c   | i   | a   | o   | \\0 |
| --- | --- | --- | --- | --- |

```c
char* s="ciao";
```
| →   |     |     | c   | i   | a   | o   | \\0 |
| --- | --- | --- | --- | --- | --- | --- | --- |

Attenzione: le variabili dichiarate con `char*` sono costanti, non vivono in memoria, quindi **non** si possono modificare.

## Operazioni

In `<string.h`:

- `size_t strlen(const char* str)` restituisce la lunghezza
- `char* strcpy(char* dest, const char* src)` copia la stringa `src` in `dest`, restituisce `dest`
- `int strcmp(const char* str1, const char* str2` confronto lessicografico, restituisce `-1`, `0` o `1`
- `char* strcat(char* dest, const char* src` concatena una copia di `src` alla `dest`, restituisce `dest`
- `char* strtok(char* str, const char* delim)` restituisce il prossimo token
