# Programmazione concorrente

Un programma concorrente contiene due o più processi (o sottoprocessi - thread) che lavorano assieme per eseguire una determinata applicazione

Ciascun (sotto)processo è un programma sequenziale

I (sotto)processi comunicano tra loro utilizzando variabili condivise (shared memory) o scambiandosi messaggi (message passing)

Astrazione: i (sotto)processi sono in esecuzione contemporanea

>[!warning]
>È un'astrazione: in realtà potrebbe non essere così.