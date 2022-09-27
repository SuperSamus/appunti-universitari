# Gestione memoria

- Programma e dati - memoria
- Zona dati
    - Dati statici
        - Variabili globali
        - Variabili statiche
    - #Stack: record di attivazione
        - 1 per ogni blocco di codice (incluso chiamate funzioni)
        - Spazio per variabili locali
    - #Heap: dati dinamici (*runtime*), frammentati
        - Memoria allocata dinamicamente, accessa coi [[puntatori]]

## Allocazione dinamica vs statica

Vantaggi
- Più controllo sulla memoria utilizzata
- Meno spreco di memoria
- Programmi più generici
- Più modularità, più facile passaggio di parametri

Svantaggi
- Complessità aggiunta per la gestione di memoria
- Possibilità di memory leak