# Verilog

- HDL (Hardware Description Language): Linguaggio di programmazione che permette di progettare un [[processore]].
	- Detto anche RTL (Register Transfer Language)
- Si può:
	- Descrivere moduli (per esempio multiplexer)
		- Sintesi ⇒ Descrizione di un circuito
			- Produrre un chip
			- [[Processore#^4d0651|FPGA]]: Circuiti programmabili
	- Scrivere test: simulazione per assicurarsi che il modulo sia scritto bene
- Da non confondere con SystemVerilog (che è un suo superset)

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

### Somma

1 bit + 1 bit + il bit di riporto iniziale. Abbiamo bisogno di due primitive: una per il risultato, e una per il carry.

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

primitive c(output z, input x, input y, input r);

  table
    0 0 0 : 0  ;
    0 0 1 : 0  ;
    0 1 0 : 0  ;
    0 1 1 : 1  ;
    1 0 0 : 0  ;
    1 0 1 : 1  ;
    1 1 0 : 1  ;
    1 1 1 : 1  ;
  endtable

endprimitive

// Da qui si può creare un modulo per collegare il tutto

module fa(output c, output z, input x, input y, input r);

  z uscita(z,x,y,r);
  c carryo(c,x,y,r);

endmodule;
```

### [[Porte logiche#^b31833|Multiplexer]]

![[Multiple multiplexers.excalidraw]]

```verilog
// Dopo aver implementato mux1
module mux4(output[3:0]z, input[3:0]x1, ..., input[3:0]x4, input [1:0]ctl);

  mux1 m4(z[3], x1[3], x2[3], x3[3], x4[3], ctl);
  mux1 m3(z[2], x1[2], x2[2], x3[2], x4[2], ctl);
  // ...

endmodule
```

## Testbench

Cosa fare:
- Creare un modulo dove si dichiarano:
	- Tante variabili di tipo `reg` quanti sono gli ingressi
	- Tanti `wire` quanti sono gli output
- Chiamare un istanza del modulo sotto test
- Creare un programma in cui si creano registri, per ve

```verilog
module testFA();

// Dichiarare tanti reg quanti sono gli ingressi
reg inx, iny, inr;
// DIchiarare tanti wire quanti gli output
wire z, c;

endmodule

FA modulotest(c, z, inx, iny, inr);

```

## Tipi di blocchi

- `initial`
	- `begin`-`end`
- `always`
	- `begin`-`end`
- `if(expr)`
- `for()`
- `case(x)`
