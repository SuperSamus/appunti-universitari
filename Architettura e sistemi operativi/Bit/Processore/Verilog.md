# Verilog

- HDL (Hardware Description Language): Linguaggio di programmazione che permette di progettare un [[processore]].
	- Detto anche RTL (Register Transfer Language)
- Si può:
	- Descrivere moduli (per esempio multiplexer)
		- Sintesi ⇒ Descrizione di un circuito
			- Produrre un chip
			- [[Processore#^4d0651|FPGA]]: Circuiti programmabili
	- Scrivere test: simulazione per assicurarsi che il modulo sia scritto bene

## Reti combinatorie

- Descrizione di un modulo
	- **Primitive**: Tabella verità
	- **Module**: Codice C-like

```verilog
primitive(   );
...
endprimitive

module(   );
...
endmodule
```

Implementiamo la [[Mappa di Karnaugh#^93d855|somma]].

```verilog
primitive z(output z, input x, input y, input r);

  table
    0 0 0 : 0  ;
    0 0 1 : 1  ;
    0 1 0 : 1  ;
    0 1 1 : 0  ;
    1 0 0 : 1  ;
    1 0 1 : 0  ;
    1 1 0 : 0  ;
    1 1 1 : 1  ;
  endtable

endprimitive
```
