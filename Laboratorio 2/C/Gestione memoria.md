## Gestione #memoria

- Programma e dati - memoria
- Zona dati
    - Dati statici
        - Variabili globali
        - Variabili statiche
    - #Stack: record di attivazione
        - 1 per ogni blocco di codice (incluso chiamate funzioni)
        - Spazio per variabili locali
    - #Heap: dati dinamici (*runtime*), frammentati
        - Memoria allocata dinamicamente, accessa coi #puntatori