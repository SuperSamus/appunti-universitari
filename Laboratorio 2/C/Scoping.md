# Scoping

- I nomi sono utilizzabili fino al blocco in cui sono dichiarati
- Le funzioni sono sempre globali nel file
- Dichiarazioni `extern`: visibili automaticamente anche in altri file
- Variabili `static` locali: persistenti tra una chiamata della funzione a l'altra
- Dichiarazioni `static` globali: visibili solo nel file in cui sono dichiarate, non si possono importare
- **Shadowing**: dichiarare una variabile con lo stesso nome in un sottoblocco