I file UNIX sono strutturati in una gerarchia standard ad albero (FHS):
- `/` è la radice (root) del FS
- `/home` è la directory per gli utenti
- `/etc` file di configurazione del sistema
- `/usr` eseguibili e librerie associati a software installati dall'amministratore
- E tanti altri

## `/dev`

"File" che sono più un astrazione per certi comportamenti:
- `/dev/zero` leggerlo fornisce uno stream di byte `NULL` (0x00)
- `/dev/null` "buco nero", qualsiasi cosa scritta lì viene buttata
- `/dev/random` leggerlo fornisce uno stream di numeri (psudo-)casuali