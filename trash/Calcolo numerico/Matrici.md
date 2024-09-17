### Matrici a predominanza diagonale

^dff2ed

Matrici dove $|a_{ii}|>∑\limits_{j≠i}a_{ij}\quad 1<i<n$

### Matrici triangolari

Sono molto comode:
- Risolverle è facile
- Trovare il determinante è facile (basta moltiplicare i valori nella diagonale, si può vedere con Laplace)
- Trovare gli [[autovalori]] è facile (sono semplicemente i valori nella diagonale)

#### Fattorizzazione LU

Divide una matrice $A$ in due matrici triangolari $L$ e $U$, tali che:
$A=LU$
Dove le diagonali di $L$ sono uguali a $1$.
Con questa proprietà, $L$ e $U$ si possono mettere in una matrice $B$ grande quanto $A$ (così non serve che occupi il doppio dello spazio):
$b_{ij}=\begin{cases}l_{ij} & \text{se } i>j \\ u_{ij} & \text{altrimenti}\end{cases}$

Un modo per ottenerla è partire da:
$A=IA$
E fare l'eliminazione di Gauss (su $A$) per ottenere $U$, mettendo i fattori in $L$: https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_(Kuttler)/02%3A_Matrices/2.10%3A_LU_Factorization

### Matrici unitarie

Sono le matrici dove $M^HM=MM^H=I$.
Dove $M^H$ è la trasposta coniugata.
Esempio: matrici di permutazione, $M=[e_1|e_2|…|e_n]$ con gli $e_i$ permutati.

### Matrice elementare di Gauss

Dato $e_k$ il $k$-esimo vettore delle basi canoniche, e $v$ un vettore dove $v_i=0$ per $i≤k$.
$A=I-ve_k^T$
($ve_k^T$ è una matrice dove la $k$-esima colonna è uguale a $v$, e le altre 0.)

Proprietà:
- È triangolare inferiore
- $A^{-1}=I+ve_k^T$
	- Infatti, $(I-ve_k^T)(I+ve_k^T)=I+ve_k^T-ve_k^T-ve_k^Tve_k^T=I$
- Per ogni $x$ dove $x_k≠0$, esiste una matrice elementare di Gauss $E$ tale che $Ex=[x_1,…,x_k,0,…,0]^T$.
- TODO
