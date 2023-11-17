La casualità è importante nella crittografia: ciò permette di rendere le chiavi *imprevedibili*.

## Complessità di Kolmogorov

Se vogliamo generare una stringa $h$ in un sistema (e.g. linguaggio di programmazione) $S_i$, vogliamo creare la più breve descrizione possibile:
$$k_{S_i}(h)=\min\{|p|:S_i(p)=h\}$$
In una sequenza casuale, questo programma conterrà la stringa stessa, e ci sarà un overhead costante per quel sistema.
$$k_{S_i}(h)=|h|+c_i$$
Possiamo eliminare la dipendenza dal sistema con un ideale sistema universale:
$$S_U(<i,p>)=S_i(p)=h$$

Come si calcola la complessità di Kolmogorov? Non si può, a causa del *paradosso di Berry*:
> "The smallest positive integer that cannot be defined in fewer than twenty English words"

Qualunque sia questo numero, potrà essere descritto da questa frase… di 14 parole.
