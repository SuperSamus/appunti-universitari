# Scoping

- I nomi sono utilizzabili fino al blocco in cui sono dichiarati
	- Le variabili vengono droppate dallo #stack alla fine del blocco
		- Usare [[puntatori]] che puntano a una variabili droppate è undefined behavior
- Le funzioni sono sempre globali nel file
- Dichiarazioni `extern`: visibili automaticamente anche in altri file
- Variabili `static` locali: persistenti tra una chiamata della funzione a l'altra
- Dichiarazioni `static` globali: visibili solo nel file in cui sono dichiarate, non si possono importare
- **Shadowing**: dichiarare una variabile con lo stesso nome in un sottoblocco