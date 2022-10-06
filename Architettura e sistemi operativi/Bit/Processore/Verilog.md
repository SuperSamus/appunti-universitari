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
// ...
endprimitive

module(   );
// ...
endmodule
```

Implementiamo la somma.

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

module fa(output c, output z, input x, input y, input r);

  z uscita(z,x,y,r);
  c carryo(c,x,y,r);

endmodule;
```



Implementiamo un [[Porte logiche#^b31833|multiplexer]]:

```verilog
// Dopo aver implementato mux1
module mux4(output[3:0]z, input[3:0]x1, ..., input 3:0x4, input [1:0]ctl);

  mux1 m4(z[3], x1[3], x2[3], /* ...,*/ x4[3], ctl);
  mux1 m3(z[2], x1[2], /* ...,*/ ctl);
  // ...

endmodule
```

Testbench

# TODO: 'sto professore scrive un programma con la penna invece che con un editor di testo, e 'un se capisce niente

```verilog
module testFA();

// Dichiarare tanti reg quanti sono gli ingressi
reg inx, iny, inr;
// DIchiarare tanti wire quanti gli output
wire z, c;

FA modulotest(c, z, mx, my);

```