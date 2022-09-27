# Processore

**Entità che permette di fare dei calcoli.**

```mermaid
flowchart LR
P(Processore) --> C("Componente (1° semestre)")
P --> G("Gestione (2° semestre) (Sistema Operativo)")
```

## Modello Von Neumann

M ↔ P (Memoria e Processore)

```
while (true) {
    **fetch** prelievo istruzione in M dall'indirizzo **PC** (Program Counter)
    **decode** decodifica -> azioni
    **exec** azioni -> eseguiamo
    aggiorniamo **PC**
    (interruzioni)
}
```

### Von Neumann bottleneck

Quando decode/exec è più veloce di fetch.

## Transistor

https://www.youtube.com/watch?v=HqhE-8xXeCQ

| Clock | Dimensioni | Componenti |
|-------|------------|------------|
| Khz   | 10 um      | 1000       |
| Ghz   | 4 nm       | 1000000    |

"Giocare" con transistor più piccoli è più veloce (gli elettroni entrano/escono più velocemente)

### Legge Moore

> Ogni 18 mesi le prestazioni raddoppiano
\- Gordon Moore


Ha smesso di essere vera da inizio anni 2000: gli elettroni per resistenza scaldano il transistor.

È il motivo per cui i processori di oggi sono multi-core.

Dobbiamo cambiare il modo in cui i processori (e di conseguenza i programmi) vanno pensati.

### Acceleratori

#### GPU

Processore che è specializzato per la grafica.

È collegato alla CPU con un bus V0, ha una propria memoria.

### CPU/Chip

Contiene

* Memoria
* GPU
* Processore
* FPGA (field-programmable gate array)
* DMA
* Bus

**SoC** System on Chip

```mermaid
flowchart TB
M <--> P
P <--> GPU
GPU <--> VM
FPGA --> P & GPU
GPU --> Monitor
```
