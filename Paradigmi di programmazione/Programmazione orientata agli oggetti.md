# Programmazione orientata agli oggetti

Creata per rendere più facile la *modularità* del programma, per esempio aumentando la quantità di *astrazione* (possibilità di scomporre il problema in sottoproblemi).

Per esempio, la *libreria standard* consente di scrivere in programma che opera su stringhe astraendo come le operazioni su stringhe siano implementate.

## Il paradigma a oggetti

- Sistema software: insieme di oggetti cooperanti
- Gli oggetti sono caratterizzati da
	- Uno stato
	- Un insieme di funzionalità
	- Identità
	- Ciclo di vita
	- Locazione (di memoria)
- Gli oggetti cooperano scambiandosi messaggi

### Lo *stato* di un oggetto

È rappresentato da un gruppo di attributi/proprietà/variabili.

**Incapsulamento**: idealmente, lo stato di un oggetto non dovrebbe essere accessibile dagli altri oggetti.

Lo stato non dovrebbe essere potuto toccato dagli altri oggetti (information hiding), come non li dovrebbe interessare come è stato implementato.

### Le funzionalità di un oggetto

Rappresentate di un gruppo di metodo/funzioni che l'oggetto mette a disposizione degli altri oggetti

I metodi descrivono il comportamento dell'oggetto, per esempio come un oggetto "risponde" ad un messaggio ricevuto da un un altro oggetto.

## Concetti

Ogni linguaggi li può implementare in modi diversi:

- Incapsulamento
- Astrazione
- Ereditarietà (come un oggetto può fare proprie la funzionalità di un altro oggetto)
- Principio di sostituzione (quando un oggetto può essere usato al posto di un altro in maniera trasparente e controllata)
- Polimorfismo (come si può processore altri oggetti indipendentemente anche tipi diversi)

## Approccio object-based

- Gli oggetti vengono trattati nel linguaggio in maniera simile ai record
- I campi (/membri/proprietà/variabili) possono essere associati a funzioni
- Una funzione in un oggetto (metodo) può accedere ai campi dell'oggetto stesso tramite il riferimento `this` (o simili)

JavaScript per esempio può modificare dinamicamente le struttura dell'oggetto (per esempio aggiungendo campi).

Questo approccio consente al programmatore di lavorare in modo flessibile (non serve scrivere il codice di una classe per avere un oggetto), e si può avere facilmente tante varianti.

Rende però difficile prevedere il tipo dell'oggetto, e ostacola i controlli statici.

## Approccio class-based

- Un linguaggio class-based prevede un concetto di *classe* a cui corrispondono determinati costrutti linguistici
- Una classe definisce il contenuto degli oggetti di un certo tipo
- Gli oggetti vengono creati successivamente come *istanze* di una certa classe

Questo approccio richiede più disciplina, in quanto ogni classe deve essere dichiarata prima di poter creare un oggetto basata su di essa (*nominal typing*), ma rende facile prevedere il tipo dell'oggetto e consente i controlli statici.

## Ereditarietà e subtyping

Funzionalità creata tramite opportuni costrutti linguistici che consente di definire una classe (o, più in generale, una tipologia di oggetti) sulla base di un'altra già esistente.

I linguaggi object-based mantengono per ogni oggetto una lista di prototipi, che sono tutti gli oggetti da cui esso eredita funzionalità.

**Subtyping nominale**: 

I linguaggi class-based consentono di definire una classe come estensione di un altra. La nuova classe eredita tutti i membri (valori e metodi) della precedente, con la possibilità di aggiungerne altri (o ridefinirne alcuni (*overriding*)).