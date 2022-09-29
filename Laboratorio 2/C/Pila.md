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

typedef Nodo *Lista;

void insert_ric(int, Lista *);
void print(Lista);
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

void print(Lista p) {
  if (p == NULL) {
    return;
  }
  printf("%d\n", p->val);
  print(p->next);
}

void print_reverse(Lista p) {
  if (p == NULL) {
    return;
  }
  print(p->next);
  printf("%d\n", p->val);
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
