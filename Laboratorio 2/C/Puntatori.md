# Puntatori

- Qualsiasi dato/istruzione che sta in memoria ha un *valore* e un *indirizzo di memoria*
- Un puntatore è una *variabile* che contiene un indirizzo di memoria
    - Ha a sua volta un indirizzo di memoria
    - Il tipo indica il dato che si aspetta di vedere nell'indirizzo a cui punta
- Dereferenziare un puntatore: `*`
- Ottenere l'indirizzo di una variabile: `&`

## Aritmetica

- `int* intPtr` punta a un numero intero
	- `intPtr+1` punta ad `intptr + i * sizeof(int)`

## Allocazione [[memoria]]

- `int a;`
	- Alloca spazio per `sizeof(int)`
	- Qual è il valore? *Non definito* (non è stato inizializzato).
- `int* aPtr;`
	- Alloca spazio per un puntatore.
	- Qual è il valore a cui punta? *Non definito* (non è stato inizializzato).
	- Cosa c'è nell'indirizzo di memoria a cui punta? *Non definito* (non è stato inizializzato).
- La libreria `stdlib` ha funzioni per allocare memoria in maniera dinamica:
	- `aPtr = malloc(sizeof(int))`
		- Non inizializza l'indirizzo a cui punta
	- `aPtr = calloc(1,sizeof(int))`
		- Inizializza `0` all'indirizzo
	- `malloc` e `calloc` ritornano `NULL` (che equivale a 0) se falliscono
- `void*`: puntatore generico
	- È il tipo restituito da `malloc` e `calloc`
	- C casta implicitamente i tipi puntatori, ma C++ non lo fa
- `free(aPtr)`: libera memoria allocata da `malloc` o `calloc`
	- Bisogna liberare la memoria quando non serve più
	- Errori comuni:
		- Non liberare memoria e perdere il puntatore: **memory leak**
		- Liberare memoria allocata in modo statico
		- Usare un puntatore dopo aver liberato la memoria

## Array di puntatori

- Possiamo avere array di puntatori
- `int* ps[10];
	- Alloca memoria per un array di 10 puntatori
- Possiamo costruire anche array dinamici di puntatori:
	- `int** ps = malloc(n*sizeof(int*))`
		- `n` puntatori a `int` non inizializzati
	- `int** ps = calloc(n, sizeof(int*))`
		- `n` puntatori a `int`, inizializzati a `0`
- Possiamo avere array multidimensionali:
	- Molto più facile passarli alle funzioni
	- Ogni riga può potenzialmente avere grandezza diversa
```c
int** a = malloc(3*sizeof(int*));
for (int i = 0; i < 2; ++i)
	a[i] = malloc(3 * sizeof(int))
```

## Puntatori a struct

```c
Stack* s = malloc(sizeof(Stack));
```

- Alloca memoria per un oggetto `Stack` (un array + un intero)
- Per accedere ai campi, usa `->`
- Uno `struct` può contenere come membri puntatori a se stesso (*self-referential*)
	- Non può invece avere riferimenti a se stesso senza puntatori (sarebbe ricorsivo, e la dimensione infinita)
	- Il puntatore invece può essere `NULL`

### Liste concatenate

Structs che tengono un riferimento al prossimo elemento

```c
struct Node {
	int val;
	struct Node* next;
}
```

![[Lista concatenata.excalidraw]]

Usabile per esempio per implementare una [[Lista]] o una [[Pila]].