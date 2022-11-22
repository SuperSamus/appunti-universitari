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

#### Logica di Hoare

Pre P Post
$\{φ\}P\{ψ\}$

Con $s$ lo stato:
$$
\cfrac{s⊨φ \quad 〈s,P〉⇒〈s',-〉}{s'⊨ψ}
$$

## Verifica delle specifiche

I test consentono di identificare errori di programmazione (rispetto alle specifiche)
- Non sono esaustivi
- Esistono strumenti di generazione automatica test

Esistono metodi di analisi statici e type checking che consentono di verificare in modo automatico la sicurezza del codice rispetto alle specifiche..

## Principio di sotituzione di Liskov

L'esistenza di una specifica consente di ragionare sul rapporto tra superclasse e sottoclasse da un punto di vista comportamentale

>[!important]
>Un oggetto di un sottotipo può sostituire un oggetto del supertipo senza influire sul comportamento dei programmi che usano il supertipo.

La sotto

Dato $C[X]$ un qualsiasi codice che utilizza $X$:

$$
\cfrac{X<Y \quad \{PRE\}C[Y]\{POST\}}{\{PRE\}C[X]\{POST\}}
$$

$t≃s⇔∀C.C[T]⇓↔C[s]⇓$