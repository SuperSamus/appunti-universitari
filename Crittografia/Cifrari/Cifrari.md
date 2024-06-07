**Cifrari per uso ristretto**: le funzioni di cifratura C e di decifrazione D sono tenute nascoste. Appena scoperte, la sicurezza è violata.

**Cifrari per uso generale**: le funzioni (pubbliche) si basano su una chiave segreta $k$. Se non si conosce, non si può fare niente.

**Attacco esauriente**: Si provano tutte le chiavi per trovare quella giusta. Spesso impracticable se il numero possibile di chiavi è gigantesco.

>[!note]
>La quantità di chiavi possibili non è sempre sufficiente a rendere la chiave sicura.
>Per esempio, se si usa una permutazione dell'alfabeto come chiave (con cui sostituire i caratteri del messaggio) si hanno $26!$ chiavi, ma le frequenze dei caratteri nel messaggio offre un forte indizio sulla chiave.
>
>I cifrari di oggi (come AES) sono considerati sicuri, ma non si sa se il metodo matematico per risolverli in tempo polinomiale non esiste o semplicemente se non è stato trovato.

**Cifrario asimmetrico**: si usa una chiave pubblica per cifrare e una chiave privata per decifrare.
- Ciò consente facilmente di comunicare in sicurezza con qualcuno senza dover scambiare alcuna chiave a priori.
- Essendo lento, viene usato per scambiare delle chiavi simmetriche.

### Cifrari storici

TODO
Facilmente rompibili con l'*analisi statistica*.

### Cifrari perfetti

TODO
$P(M=m|C=c)=P(M=m)$

**Teorema di Shannon**: affinché un cifrario possa essere perfetto, il numero delle chiavi deve essere uguale o maggiore del numero dei messaggi.

Per confondere il criptoanalista, è opportuno che molte coppie $(m,k)$ corrispondono allo stesso crittogramma.
