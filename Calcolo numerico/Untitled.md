$g(x)=\log(x+1)$

$f(x)=\frac{2x}{x+2}\quad -\frac{1}{2}≤x≤0$

Errore analitico di approssimazione $ε_{AN}=\frac{f(x)-g(x)}{g(x)}$

Cosa c'entrano queste funzioni tra loro? Si può vedere se sono simili con lo sviluppo di Taylor (nessuna delle due ora è un polinomio).

Con $x_0=0$. L'ultimo pezzo è il *resto di Lagrange*.

$g(x)=g(0)+g'(0)x+\frac{g''(0)}{2}x^2+\frac{g'''(ξ)}{6}x^3\quad x≤ξ≤0$
- $g'(x)=\frac{1}{x+1}$
- $g''(x)=-\frac{1}{(x+1)^2}$
- $g'''(x)=\frac{2}{(x+1)^3}$
$g(x)=0+x-\frac{x^2}{2}+\frac{1}{(ξ+1)^3}\frac{x^3}{3}$

$f(x)=f(0)+f'(0)x+\frac{f''(0)}{2}x^2+\frac{f'''(η)}{6}x^3\quad x≤ξ≤0$
- $f'(x)=\frac{2(x+2)-2x}{(x+2)^2}=\frac{4}{(x+2)^2}$
- $f''(x)=-\frac{8}{(x+2)^3}$
- $f'''(x)=\frac{24}{(x+2)^4}$
$f(x)=0+x-\frac{x^2}{2}+\frac{4}{(η+2)^4}x^3$

Vogliamo diminuire il più possibile l'errore.

$|f(x)-g(x)|=|\frac{x^3}{3}||(\frac{12}{(η+2)^4}-\frac{1}{(ξ+1)^3})|≤\frac{|x^3|}{3}(\frac{12}{(η+2)^4}-\frac{1}{(ξ+1)^3})≤\frac{|x^3|}{3}(\frac{12*2^4}{3^4}+2^3=$
