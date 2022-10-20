# Unix

## File

I file UNIX sono strutturati in una gerarchia standard ad albero (FHS):
- `/` è la radice (root) del FS
- `/home` è la directory per gli utenti
- `/etc` file di configurazione del sistema
- `/usr` eseguibili e librerie associati a software installati dall'amministratore
- E tanti altri

### `/dev`

"File" che sono più un astrazione per certi comportamenti:
- `/dev/zero` leggerlo fornisce uno stream di byte `NULL` (`0x00`)
- `/dev/null` "buco nero", qualsiasi cosa scritta lì viene buttata
- `/dev/random` leggerlo fornisce uno stream di numeri (pseudo-)casuali
- E tanti altri

### Diritti e permessi

Gli utenti di un sistema Unix accede ai file in base ai permessi:
- Lettura `r`
- Scrittura `w`
- Esecuzione `x`

I permessi sono assegnati al:
- Proprietario
- Gruppo
- Altri

Si possono visualizzare con `ls -l`, e cambiare:
- Permessi con `chmod` 
- Proprietario con `chown`
- Gruppo con `chgrp`