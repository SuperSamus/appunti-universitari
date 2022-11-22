## Fasi della progettazione e sviluppo

Idealmente lo sviluppo dovrebbe attraversare queste fasi:
- Definizione della gerarchia di classi
- Identificazione dei membri pubblici
- Definizione delle specifiche di ogni metodo pubblico
- Implementazione di programmi di testing
- Definizione dei membri privati
- Implementazione del codice delle classi

### Definire le specifiche

Definire le specifiche di una classe significa esprimere in modo non ambiguo il comportamento atteso dei suoi metodi pubblici.

Come fare:
- Aggiungendo opportuni commenti al codice
- Esprimendo delle condizioni sui parametri e sulle variabili che siano verificabili o testabili (per esempio `assert`)

Per esempio: TODO
```java
public class IntSet {
    public IntSet(int capacity) {
        // REQUIRES: capacity non negativo
        // EFFECTS: crea un insieme vuoto che può ospitare capacity aggiuntivi
    }

    /**
     * Aggiunge un elemento all'insieme
     * @param elem
    */
    public boolean add(int elem) throws FullSetException {
        // ...
    }

    public boolean contains(int elem) {
        // REQUIRES:
        // EFFECTS: restituisce true se elem p presente nel set...
    }
}
```

### Precondizioni e postcondizioni

Per ogni metodo, le specifiche indicano:
- **Precondizioni** (`// REQUIRES`): condizioni sui parametri e sul valore delle variabili che devono essere soddisfatte all'inizio dell'esecuzione del metodo
- **Postcondizioni** (`// EFFECTS`): condizione sul risultato e sul valore delle variabili che devono essere soddisfatte al termine dell'esecuzione del metodo, assumendo che all'inizio fossero vere le precondizioni.