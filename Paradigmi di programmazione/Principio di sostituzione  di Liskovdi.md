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

## Principio di sostituzione di Liskov

L'esistenza di una specifica consente di ragionare sul rapporto tra superclasse e sottoclasse da un punto di vista comportamentale.

>[!important]
>Un oggetto di un sottotipo può sostituire un oggetto del supertipo senza influire sul comportamento dei programmi che usano il supertipo.

La sottoclasse deve soddisfare le specifiche della superclasse.

Dato $C[X]$ un qualsiasi codice che utilizza $X$:

$$
\cfrac{X<Y \quad \{PRE\}C[Y]\{POST\}}{\{PRE\}C[X]\{POST\}}
$$

$t≃s⇔∀C.C[T]⇓↔C[s]⇓$

Questo principio va oltre il semplice concetto di sottotipo sostituibile per subsumption
- Esprime una relazione tra i comportamenti degli oggetti dei due tipi
- La relazione deve valere per tutti i possibili contesti in cui la sostituzione può avvenire

Problemi:
- I contesti possibili sono infiniti
- I contesti sono programmi

#### Regole indotte dal LSP

Il principio di sostituzione di Liskov nella pratica si trace in un insieme di regola da seguire:
- La regola della segatura
	- Gli oggetti del sottotipo devono avere tutti i metodi del supertipo
	- Le segnature (firme) dei metodi del sottotipo devono essere compatibili con le segnature dei corrispondenti metodi del super tipo
- Le regola dei metodi
	- Le chiamate dei metodi del sottotipo devono comportarsi come le chiamate dei corrispondenti metodi del supertipo
- La regola delle proprietà
	- Il sottotipo deve preservare tutte le proprietà che possono essere provate sugli oggetti del supertipo

#### Regola della segnatura

>[!important]
> - Gli oggetti del sottotipo dei devono avere tutti i metodi del supertipo
> - Le segnature (firme) dei metodi del sottotipo devono essere compatibili con le segnature dei corrispondenti metodi del supertipo

Le presenza di tutti i metodi è garantita dal compilatore tramite i meccanismi di ereditarietà.

In caso di overriding, il metodo nella sottoclasse:
- Deve avere la stessa firma del metodo della superclasse
- Può sollevare meno eccezioni
- Può avere un return type più specifico (sottotipo di quello del metodo della superclasse
