Fasi:
- Analisi dei requisiti
- Specifica
- Progettazione
- Implementazione
- Integrazione
- Mantenimento
- Ritiro

Se si lavora in gruppo, il processo va modellizzato (suddiviso in attività).

- Modelli sequenziali
	- **Modello a cascata**
	- **Modello a V**
- Modelli iterativi
	- **Rapid prototyping**
	- **Modello incrementale**
	- **Modello a spirale**
	- **Unified process**
	- **Agile**
		- **eXtreme programming**
		- **Scrum**
			- Divide il lavoro in *obiettivi* da completare in uno *sprint* (di solito 15 giorni), dopo di che viene fatto uno stand-up meeting per discutere come è andato lo sprint e organizzare il prossimo.

### Dominio

Il contesto in cui il software opera.
- Glossario
- Modello statico
	- Entità
	- Relazioni
- Modello dinamico
	- Processi
	- Comportamenti

**Unified Modeling Language (UML)**: linguaggio di modellazione unificato

### Requisito

Una condizione o una capacità necessaria a un utente per risolvere un problema.
- Requisito funzionale
- Requisito non funzionale

I requisiti si:
- *Acquisiscono* tramite interviste
	- Casi d'uso
	- User stories
- *Elaborano* scrivendo una bozza
- *Convalidano* correggendo omissioni, inconsistenze, ambiguità, sinonimi, omonimi, dettagli tecnici, ridondanza…
	- Si correggono incontrando il committente
- *Negoziano* assegnando le priorità
- *Gestiscono* assegnandoli un identificatore unico

Diagramma dei casi d'uso:
- Attori
- Casi d'uso
- Relazioni
	- Hanno una *molteplicità* (tanti/uno solo/…)
	- *Aggregazione*: una relazione nelle quali le classi parte hanno un significato da sole
	- *Composizione*: una relazione in cui le classi parte hanno significato solo se legate alla classe tutto
- Confine del sistema

I vari elementi si possono *generalizzare*, così che possano aver figli che ereditano da essi. Questo permette per esempio di avere un solo attore principale.

**Scenario**: istanza di un caso d’uso. Hanno una pre-condizione, e dopo la sequenza principale di eventi portano alla post-condizione
- Pre-condizioni e post-condizioni *non* sono azioni

I casi d'uso possono:
- *Includere* altri casi d'uso che fanno parte dell'interazione
- *Estendere* altri d'uso, in modo da ampliarne le loro funzionalità opzionali
	- Si può collegare un vincolo all'estensione, così che venga automaticamente utilizzata se il vincolo viene soddisfatto
		 - Esempio: per una banca, il caso d'uso "mostra nuovo bilancio", estende "deposita fondi" e "ritira fondi", con la condizione "il terminale ha uno schermo"

### Classe

Cattura un concetto nel dominio del problema o della realizzazione.
Descrive un insieme di oggetti con caratteristiche simili.

Gli oggetti sono entità caratterizzate da:
- Identità
- Stato
- Comportamento
	- Le operazioni e i dettagli di implementazione sono omessi, in quanto dettaglio eccessivo

### Diagrammi di attività

Modellano un'*attività* relativa a una qualsiasi entità o collezione di entità.
Il contenuto di un'attività è un grafo diretto i cui:
- I nodi rappresentano le componenti dell'attività, come le *azioni* o i *nodi di controllo*
	- Le azioni sono *atomiche*
	- I nodi di controllo sono per esempio *inizio*, *fine attività* o *fine flusso*
- Gli archi rappresentano il *control flow*
	- Un *nodo decisione* (choice) porta il token sulla freccia uscente condizione vera
		- Le condizioni di guardia sono: 
			- Mutualmente esclusive
			- Esaustive (ce ne deve essere una vera)
		- La strada si riunisce con il *nodo fusione* (merge)
	- *Fork* moltiplica i token: ne "produce" uno per ogni freccia uscente
		- *Join* consuma i token: attende che arrivino tutta dalla freccia entrante, e ne esce solo uno
			- Se si usa invece un *nodo fusione*, le attività dopo di esso verranno eseguite più volte (una volta per token)
		- Non per forza dei percorsi separati si devono riunire
			- Il nodo *fine attività* termina l'intera attività appena un token ci arriva. Il nodo *fine flusso* fa continuare il percorso ai token non ancora arrivati.

>[!warning]
>Nella semantica UML, multiple frecce uscenti/entranti in un nodo azione significano fork/join.
>I nodi choice/merge vanno disegnati explicitamente.

Ci sono anche nodi *eventi* e *segnali*:
- Se un token arriva a un nodo evento, si blocca finché non verrà inviato il segnale
- Se un nodo evento non ha alcun arco entrante, genera un token ogni volta che viene inviato il segnale
- L'evento può anche essere *temporale* (assoluto o relativo)

Inoltre, un diagramma può contenere:
- Riferimenti a *attività secondarie* (sotto-attività)
- Partizioni, per assegnare responsabilità alle azioni

### Macchina a stati

Transizione:
- L'uscita da uno stato
- Definisce la risposta dell'oggetto all'occorrenza di un *evento*
	- Operazione o segnale
	- Evento di variazione (when)
	- Evento temporale (after)
- Non-determinismo ammesso (viene fatta una scelta non-deterministicamente, non esiste il fork)
- Comporta l'esecuzione di azioni specificate:
	- Azione di entrata: eseguita all'ingresso in uno stato
	- Azione di uscita: eseguita all'uscita di uno stato
	- Transizione interna: risposta ad un evento

Attività interna (Do-activity):
- Eseguita in modo continuato mentre l’oggetto si trova in quello stato
- Senza necessità di un evento scatenante
- Al contrario di tutte le altre azioni che sono atomiche:
	- Consuma del tempo
	- Può essere interrotta (quando un evento fa uscire dallo stato)

Stato composito sequenziale:
- Una transizione su di esso prosegue in tutti i suoi stati iniziali (di default)
- Si può uscire arrivando allo stato finale (che porta alla transizione di completamento), o se un altro evento scatena una transizione dal bordo
- Le transizioni (sia di entrata che di uscita) possono "bucare" il bordo
- Si può opzionalmente definire in un diagramma a parte (*sottomacchina*)
	- Come alternativa al "bucare" il bordo, si definiscono i punti di ingresso (hanno stati iniziali diversi) o di uscita (per una transizione diversa)
- *History* è uno pseudo-stato che porta allo stato in cui la macchina era quando si è usciti l'ultima volta, con uno stato di default nel caso non sia applicabile (e.g. primo ingresso)

Stato composito parallelo:
- Sottostati attivi contemporaneamente, uno per regione
- Una qualsiasi transizione che porta fuori dallo stato composito (sia per normale evento, che per "buco"), fa uscire da tutti i sottostati

Giunzione:
- Pseudo-stato simile a choice, ma le guardie non hanno bisogno di essere esaustive
	- Se nessuna guardia è vera, non viene fatto nessuna transizione