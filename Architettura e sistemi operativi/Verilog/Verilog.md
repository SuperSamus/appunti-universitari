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

// full add
module fa(output c, output z, input x, input y, input r);

  z uscita(z,x,y,r);
  c carryo(c,x,y,r);

endmodule;

// Sfruttiamo il modulo fa per sommare coppie di 8 bit
module adder(output carry, output [7:0] z, input [7:0] a, input [7:0] b);
    genvar i;
    wire [6:0] c;
    
    fa f0(c[0],z[0],a[0],b[0],1'b0);
    fa f1(c[1],z[1],a[1],b[1],c[0]);
    fa f2(c[2],z[2],a[2],b[2],c[1]);
    fa f3(c[3],z[3],a[3],b[3],c[2]);
    fa f4(c[4],z[4],a[4],b[4],c[3]);
    fa f5(c[5],z[5],a[5],b[5],c[4]);
    fa f6(c[6],z[6],a[6],b[6],c[5]);
    fa f7(carry,z[7],a[7],b[7],c[6]);
endmodule
```

### [[Porte logiche#^b31833|Multiplexer]]

![[Multiple multiplexers.excalidraw]]

```verilog
// Dopo aver implementato mux1
module mux4(output [3:0] z, input [3:0] x1, ..., input [3:0] x4, input [1:0] ctl);

  mux1 m4(z[3], x1[3], x2[3], x3[3], x4[3], ctl);
  mux1 m3(z[2], x1[2], x2[2], x3[2], x4[2], ctl);
  // ...

endmodule

```

## Testbench

Cosa fare:
```verilog
// Creare un modulo dove si dichiarano
module testFA();
    // tanti reg quanti sono gli ingressi
    reg inx, iny, inr;
    // tanti wire quanti gli output
    wire z, c;
endmodule

// Chiamare un istanza del modulo sotto test
FA modulotest(c, z, inx, iny, inr);

// Creare un programma in cui si creano registri, per vedere che fine fanno i wire
initial begin
    // Per esempio
    inx=0; iny=0; inr=0;
    #1 inx=1;
end

// Direttive
$dumpfile(" ");
$dumpvars;
// ...
$finish;
```

## Tipi di blocchi

- `initial`
	- `begin`-`end`
- `always`
	- `begin`-`end`
- `if(expr)`
- `for()`
- `case(x)`
