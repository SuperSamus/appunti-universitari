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
module adder(output carry, output [N-1:0] z, input [N-1:0] a, input [N-1:0] b);

    parameter N = 8;

    wire [N-2:0] c;

    // Il primo ha un carry pari a 0
    fa f0(c[0],z[0],a[0],b[0],1'b0);
    // Quelli intermedi prendono il riporto dal precedente e propagano il riporto a quelli successivi
    generate
        genvar i;
        for(i=1;i<N-1;i=1+1)
	        fa f(c[i], z[i], a[i], b[i], c[i-1]);
	endgenerate
    // L'ultimo genera il segnale di riporto del modulo intero
    fa f7(carry,z[N-1],a[N-1],b[N-1],c[N-2]);
endmodule
```

Nota che Verilog permette di usare scorciatoie per evitare di creare le prime due primitive:

```Verilog
module fa(output c, output z, input x, input y, input r);
    assign { c, z } = a + b + r;
endmodule;
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

## Behavior

I vari `begin-end` si possono omettere se il blocco si applica solo al comando successivo.

- `initial begin`
	- `comandi`
		- Vengono eseguiti quando accendiamo il modulo
	- `end`
- `always@(event) begin`
	- `comandi`
		- Vengono eseguiti ogni volta che `event`
		- Se `@(event)` viene omesso, vengono ripetuto in continuazione
	- `end`
- `if(expr) begin`
	- `comandi`
	- `end`
	- Può essere seguito da `else begin`
		- `comandi`
		- `end`
- `for(inizio; condizione; passo) begin
	- `comandi`
	- `end`
- `case(expr)`
	- `possibilità1: comando`
	- `possibilità2: begin comandi end`
	- `default: comando`
	- `endcase`
- `$display`
	- Equivalente di `printf`
- `$monitor`
	- Stampa la stringa ogni volte che una delle variabili cambia

Assegna uno alla volta:

```Verilog
a = 1;
b = 0;
```

Assegna contemporaneamente (non bloccante):

```Verilog
a <= 1;
b <= 0;
```

Quest'ultimo si può usare per esempio per scambiare due variabili, senza necessità di usare una terza variabile temporanea:

```Verilog
a <= b;
b <= a;
```

## Altri esempi

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

### [[Porte logiche#^93c33a|Codificatore]]

```verilog
primitive z1(output z, input a, input b, input c, input d);
    table
        0 0 0 0 : 0
        0 0 0 1 : 0
        // ...
        0 1 0 0 : 1
        1 0 0 0 : 1
    endtable
endprimitive

// Alternativamente 

module z1(output z, input a, input b, input c, input d);
    assign z = ~a && b && ~ c && ~d || a && ~b && ~c && ~d
endmodule

// Alternativamente

module z1(output reg z, input a, input b, input c, input d);
    always@(a or b or c or d) begin
        case ({a,b,c,d})
            4'b1000, 4'b0100: z = 1
            default: z = 0
        endcase
    end
endmodule

// Se vogliamo fare entrambi i bit di output

module cod(output reg [1:0] z, input a, input b, input c, input d);
    always@(a or b or c or d) begin
        case ({a,b,c,d})
            4'b1000: z = 2'b11
            4'b0100: z = 2'b10
            4'b0010: z = 2'b01
            default: z = 2'b00
        endcase
    end
endmodule
```
