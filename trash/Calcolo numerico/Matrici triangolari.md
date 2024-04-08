Sono molto comode:
- Risolverle è facile, dato che non serve l'eliminazione di Gauss
- Trovare il determinante è facile (basta moltiplicare i valori nella diagonale, si può vedre con Laplace)

## Fattorizzazione LU

Divide una matrice $A$ in due matrici triangolari $L$ e $U$, tali che:
$A=LU$
Dove le diagonali di $L$ sono uguali a $1$.
Con questa proprietà, $L$ e $U$ si possono mettere in una matrice $B$ grande quanto $A$ (così non serve che occupi il doppio dello spazio):
$b_{ij}=\begin{cases}l_{ij} & \text{se } i>j \\ u_{ij} & \text{altrimenti}\end{cases}$

Un modo per ottenerla è partire da:
$A=IA$
E fare l'eliminazione di Gauss (su $A$) per ottenere $U$, mettendo i fattori in $L$: https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_(Kuttler)/02%3A_Matrices/2.10%3A_LU_Factorization

