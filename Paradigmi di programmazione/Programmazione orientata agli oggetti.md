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

- Incpsulamento
- Astrazione
- Ereditarietà (come un oggetto può fare proprie la funzionalità di un altro oggetto)
- Principio di sostituzione (quando un oggetto può essere usato al posto di un altro in maniera trasparente e controllata)
- Polimorfismo (come si può processore altri oggetti indipendentemente anche tipi diversi)