## Lecture 3 

### **General Framework for network/model training**:
* In principle networks can approximate any function however in practice it is easier if pre-processing if applied first.

* Pre-processing need not be optimal but applying human intelligence can enhance the performance of the **AI** in network trainig.

* Post-processing often only involves passively re-mapping the network output into its raw form.

Input data $\rightarrow$ Pre-processing $\rightarrow$  Network/ model optimization $\rightarrow$ Post-processing $\rightarrow$  Output data 

### **Pre-processing data**:

#### Input normalisation:
- Normalse data to be of the same scale and have 0 mean.
- Useful for network training, and visual inspection.

#### Dimensionality reduction:
- Use math to efficiently reduce No. of dimensions.
- Define a few variables that are combinations of the raw variables and account for most of the variance. 
- (Some information will be lost).

#### Feature selection: 
- Include/exclude attributes in the data without changing them.
- Automatically or manually.
- (Some information will be lost).

#### Feature extraction:
- Use combination of input variables.
- This approach can incorporate 1,2,3.

### **Character Recognition Example**:
For a 256 x 256 character we have 65536 pixels. One input for each pixel is bad for many reasons:
- Poor **generalisation**: Data set would have to be vast to be able to properly constrain all the parameters (**Curse of Dimensionality**).
- Computational Cost: Takes a long time to train.

### **Input Normalisation**:

If variation and scale of some variables is much greater than variation in others, this can bias feature extraction, and hinder model-fiting.

Therefore, pre-process data to give 0 mean and unit variance to each variable via simple transformation: 
- $x \rightarrow \frac{x- \mu}{\sigma}$
- where $\mu$ is the mean and $\sigma$ is the standard deviation.
- (Individually for each variable).

Normalisation, as well as improving the process of machine learning, is useful for interpretation of models.
<br> It will maintain correlations.

### **Whitening**:
- Often optimal to redefine features during pre-processing, no network training/ model fitting is applied to features that are not correlated. This is called **whitening**.
- Often achieved during dimensionality reduction - e.g. PCA.

Whitening defines a new frame of reference so that in that new frame the features are no longer correlated.

#### Formula: 
- $x' = \Lambda^{-\frac{1}{2}}U^T(x - \mu)$
- Where $U$ is a matrix whose columns are the eigenvectors $u_i$ of $\Sigma$, the covariance matrix of the data, and $\Lambda$ a matrix with the corresponding eigenvalues $\lambda_i$ on the diagonal and $\mu$ is the mean of the data.

### **Eigenvectors and eigenvalues**:
Given a M x M matrix A if: $A\underline x = \lambda\underline x$ for some scalar $\lambda \neq 0, then <u>x</u> is an eigenvector with eigenvalue $\lambda$.
<br>
If $A\underline x = \lambda\underline x$ then $A2\underline x = \lambda2\underline x$ it follows <u>x</u> is not unique so it is common to scale <u>x</u> to unit length.
* Intuition: The direction of <u>x</u> is unchanged by being transformed by A so it "reflects" the principal axis of transformation.

### **Eigenvector Facts**:
* If A is symmetric (true if A is the covariance matrix), the eigenvectors $u$ will be orthogonal and unit length. And the complete set of eigenvectors can be used as a new frame of reference for the data.
* $\underline x = \sum\limits_{i=1}^{d} z_i \underline u_i$
* Expressed in the new coordinate system the matrix becomes diagonal, with the eigenvalues down the diagonal.

### **Covariance Matrix**:
* Covariance Matrix: 
    * $\Sigma_{ij} = \frac{1}{N}\sum\limits_{n=1}^{N}(x_{i,n} - \overline x_i)(x_{j,n} - \overline x_j)$
* Diagonal terms are the variances of each feature:
    - $\Sigma_{ii} = \frac{1}{N}\sum\limits_{n=1}^{N}(x_{i,n} - \overline x_i)^2$

Off-diagonal terms are the covariances between pairs of features.<br> Covariance is a measure of correlation.

Eigenvalues of the covariance matrix are equal to the variances in the frame of reference in which there are no correlations.

### **Input Normalizations - some variations**:
* Input normalization best for Gaussian (normal) distributed data (This assumption does not always hold).

* If a variable is bounded, you might want to transform the range to a uniform scale (0 to 1 e.g.) or binarise (this will lose information however).

* Sometimes logarithmic transformation is needed is data is skewed.

### **To Summise**:
* **Input Normalization** aids visualisation - usually improves performance of model training.

* **Dimensionality Reduction/ Feature Selection/ Feature Extraction**:
    * **Reduces overfitting** - Less redundant data means less opportunity to make decisions based on noise.

    * **Improves Accuracy** - Less misleading data means modeling accuracy improves.

    * **Reduces Training Time** - Fewer data points reduce algo. complexity and algos. train faster.