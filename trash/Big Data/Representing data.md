Datasets are not only very large, but they also have a huge dimensionality. For it to be workable, it needs to be reduced.

### PCA: Principal Component Analysis

Aims to minimize the covariance of the features.

From the dataset $X=\begin{bmatrix}v_1,v_2,…,v_n\end{bmatrix}$, do the mean-centering to get the matrix $\bar{X}$.
Its covariance matrix is $\bar{Σ}=\frac{\bar{X}\bar{X^T}}{n-1}$, which is symmetrical, thus it has a spectral decomposition.
We want to find an $A$ to build a new matrix representing the dataset $\hat{X}=A\bar{X}$, such that the covariance matrix $\hat{Σ}=\frac{\hat{X}\hat{X^T}}{n-1}$ is diagonal.

$$\hat{Σ}=\frac{\hat{X}\hat{X^T}}{n-1}=\frac{A\bar{X}(A\bar{X})^T}{n-1}=\frac{A\bar{X}\bar{X}^TA^T}{n-1}=A\bar{Σ}A^T=A(\bar{V}\bar{Λ}\bar{V}^T)A^T$$

- $\bar{Λ}$ is the eigenvalues diagonal
- $\bar{V}$ consists of the eigenvectors of $\bar{Σ}$.
	- Due to the spectral theory, because the latter is symmetrical, $\bar{V}$ is orthogonal
$A$ is unknown, so… what if it was $A=\bar{V}^T$?

$$\hat{Σ}=A\bar{V}\bar{Λ}\bar{V}^TA^T=\bar{V}^T\bar{V}\bar{Λ}\bar{V}^T\bar{V}=\bar{Λ}$$

Which, as said before, is diagonal.
