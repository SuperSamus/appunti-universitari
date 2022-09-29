# Pila

Struttura LIFO (Last In First Out).

Di solito contiene le seguenti funzionalità:
- `push`
- `pop`
- `peak`
- `size`

Implementazione con [[Lista concatenata.excalidraw|Linked List]]:

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct N {
  int val;
  struct N *next;
} Nodo;

typedef Nodo *Pila;

void push(int, Pila *);

// Pila push(int, Pila) non è una buona idea in C
// Si creerebbero due pile con puntatori che puntano alle stesse cose
// Sarebbe un disastro di aliasing

int pop(Pila*);
int peek(Pila);
void print(Pila);
void print_reverse(Pila);
int size(Pila);

int main() {
  Pila p = NULL;
  int x;
  do {
    scanf("%d", &x);
    push(x, &p);
  } while (x >= 0);

  printf("La pila contiene %d elementi:\n", size(p));
  print(p);
  printf("L'elemento successivo nella pila è: %d\n", peek(p));
  x = pop(&p);
  printf("Ho rimosso l'elemento %d\n", x);
  printf("La pila contiene %d elementi:\n", size(p));
  print(p);
}

int pop(Pila *p) {
  if (*p == NULL) {
    return 0;
  }

  Nodo *temp = *p;
  int val = (*p)->val;
  *p = (*p)->next;
  free(temp);
  return val;
}

int peek(Pila p) {
  if (p == NULL) {
    return 0;
  }
  return p->val;
}

void push(int n, Pila *p) {
  Nodo *nd = malloc(sizeof(Nodo));
  if (nd == NULL) {
    exit(1);
  }

  nd->val = n;
  nd->next = *p;
  *p = nd;
}

void print(Pila p) {
  if (p == NULL) {
    return;
  }
  printf("%d\n", p->val);
  print(p->next);
}

void print_reverse(Pila p) {
  if (p == NULL) {
    return;
  }
  print(p->next);
  printf("%d\n", p->val);
}

int size(Pila p) {
  if (p == NULL) {
    return 0;
  }
  return 1 + size(p->next);
}
```

## Lista ordinata

```c
#include <stdio.h>
#include <stdlib.h>

typedef struct N {
  int val;
  struct N *next;
} Nodo;

typedef Nodo *Lista;

void insert_ric(int, Lista *);
void insert(int, Lista *);

int main() {
  Lista l = NULL;
  int x;
  do {
    scanf("%d", &x);
    insert(x, &l);
  } while (x >= 0);

  print(l);
}

void insert_ric(int x, Lista *l) {
  if ((*l) == NULL || (*l)->val > x) {
    Nodo *nuovo = malloc(sizeof(Nodo));
    if (nuovo == NULL) {
      printf("Fatal error");
      exit(1);
    }
    nuovo->val = x;
    nuovo->next = *l;

    *l = nuovo;
  } else {
    insert_ric(x, &(*l)->next);
  }
}

void insert(int x, Lista *l) {
  Nodo *prec, *succ, *nuovo;

  nuovo = malloc(sizeof(Nodo));
  if (nuovo == NULL) {
    printf("Fatal error");
    exit(1);
  }

  nuovo->val = x;
  nuovo->next = NULL;

  prec = NULL;
  succ = *l;

  while (succ != NULL && succ->val < x) {
    prec = succ;
    succ = succ->next;
  }

  nuovo->next = succ;
  if (prec != NULL) {
    prec->next = nuovo;
  } else {
    *l = nuovo;
  }
}
```
