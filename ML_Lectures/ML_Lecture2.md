## Lecture 2

### **Instances and Instance Spaces:**
* Data consists of a set of instances. Each instance represents an object of interest.

* Set of all possible instances is the **instance space**. 
    - e.g. set of all email messages written in English
    - set of human faces.

* Notation:
    - Instance Space is denoted by $X$.
    - An individual instance will be denoted by $x$.
    - $x \in X$

### **Labels and Label Spaces:**
* In supervised problems, each instance is associated with a label.

* Set of all labels is called **label space**.
    - class labels $$C$$ in <u> classification</u> tasks. e.g. $C$ = {frogs, badgers}.
    - real numbers $\subseteq R$ in <u> regression</u> tasks. e.g. pixel coordinate.

* Notation:
    - arbitary label space denoted by $Y$.
    - Labelling function $f : X \rightarrow Y$ maps from **instances** to **labels**.
    - Label associated with a given instance $x$ denoted by $f(x)$.

### **Binary Classification:**
* Simplest case deals with just **2** class labels.
    - positive ( + or +1 )
    - negative ( - or -1 )

* Convention - the class of interest is **positive**.

* Binary classification task is to label instances with one or other of the class labels.

* Can also be understood as **concept identification**.
    - e.g. identifying faces in photographs.

### **Learning a classifier:**
* In practice the true classification of a function $f$ is unknown.

* We have a **training set** of **labelled instances**, that is ( $x, f(x)$ ).
    - A set of manually annotated examples.

* These examples are used to learn a model $\hat{f}:  X \rightarrow C$

* $\hat{f}$ approximates the true classification function $f$.
    - Should follow the training examples closely.
    - Should generalise to whole of the instance space $X$.

### **Binary Classification - Assessing Performance:**
* For a **learned** binary classifier, $\hat{f}$ approximates the true classification function $f$.
    - $\hat{f}$ will not exactly be the same function as $f$.
    - $\hat{f}$ will make errors in assigning class labels to instances.

### **Training/Validation Split** 
* Most important is whether the classifer has learned to <u>generalize</u>.

* Evalutated by assessing classification accuracy on a **validation set**.
    - A set of labelled data that <u> was not</u> used for training.
    - Assumed that data was chosen randomly from a set of images sharing common characteristics.
    - Often referred to as **independently** and **identically distributed** (or iid).
    - If validation set is unusual in some way, it will be a poor measure of classifier quality.

* Penalises model <u> overfitting</u> - i.e. just understanding the training set really well.

### **K-Fold Cross-Validation**:
* Dataset split into K sections.

* Each run (K total) one fold is removed from the total sections (training set) and used to validate/test the model. 

* Typically average is taken of the accuracies for an idea of expected accuracy.

* Usually 5/7 folds are used however if model takes a long time to train a smaller K value is used.

### **Peaking and maintaining a test set**:
* Validation sets are useful however it means we might be making model choices based on the validation set.

* For this reason a seperate test set is sometimes used to evaluate final performance (Test set not looked at till the end).

* Useful when building real-life systems and need to give a predication on its accuracy. 

* Mixing the training/validation/testing datasets is called **peeking** - results in an over-inflation of goodness of our model.

### **Data Insights**:
* Rubbish in $\rightarrow$ Rubbish out. ML problems require curation of the dataset.

* Inspecting data manually - plotting / dimensionality reduction tools - can help to understand.

* Data labels <u> always</u> contain mistakes or aimbiguities, so dont blindly trust them.

* Always choose your train/test/split randomly otherwise odd differences may be introduced. e.g. first half of dataset may only contain cats.

### **Binary Classification**:
#### Assessing Performance:
* Use **contingency table** / **confusion matrix**:

| | **Predicted +** | **Predicted -**| | 
|---:|:---:|:---:|:---|
**Actual +**| 30 | 20| **50**|
**Actual -**| 10 | 90| **100**|
| | **40**| **110**| **150**|

#### Accuracy and Error:
* **Accuracy** - Proportion of correctly predicted instances.
* **Error** - Proportion of incorrectly predicted instances.

From above example:
* the accuracy on our validation set of 150 instances is (30 + 90)/150 = 0.8 therefore accuracy of 80%.
* Error rate on validation set: (10 + 20)/150 = 0.2 -> (20%).

#### More Useful Metrics:
Whilst accuracy is important it is not always realistic that both classes are of equal importance. E.g. facial recognition system:
* Take the +ve class as one identity and the -ve class the remainder identities. 
* Trade off between always correctly identifying the +ve class and mis-identifing the -ve class.
* On the side of caution i.e. always correctly find the +ve class this creates the chance of incorrectly finding people from the -ve class.
    - Current issue with facial recognition and can be met with heavily negative response.

E.g. medical diagnosis system:
* +ve class as bad cancer (requires surgery), -ve class benign (no surgery).
* Trade off between always correctly correctly identifying the +ve class and mis-identifying the -ve class.
* etc.

#### Per-Class Accuracy:
* **True positive rate**: Proportion of correctly predicted +ve instances.
* **True negative rate**: Proportion of correctly predicted -ve instances.

Using the same matrix:
| | **Predicted +** | **Predicted -**| | 
|---:|:---:|:---:|:---|
**Actual +**| 30 | 20| **50**|
**Actual -**| 10 | 90| **100**|
| | **40**| **110**| **150**|

TPR (***Sensitivity***) on validation set is 30/50 = 0.6.<br>TNR (***Specificty***) on validation set is 90/100 = 0.9.

#### Per-Class Inaccuracy:
* **False positive rate**: Proportion of incorrectly predicted -ive instances.
* **False negative rate**: Proportion of incorrectly predicted +ve instances.

FPR on validation set is 10/100 = 0.1.
<br>FNR on validation set is 20/50 = 0.4.

#### Precision and Recall: 
* **Precision**: Proportion of +ve predicitions that are correct.
* **Recall**: Proportion of +ve *instances* that are predicted (**TPR**)

<br>

### **Multi-Class Classification**: 
* One-versus-rest (**OVR**): learn $k$ different binary classifiers:
    - First separates $C_{1}$ from $C_{2},...,C_{k}$
    - Second separates $C_{2}$ from $C_{1},C_{3},...C_{k}$ etc.
    - i-th classifier separates $C_{i}$ from all other classes.
* One-versus-one (**OVO**): learn $k(k-1)/2$ binary classifiers:
    - one classifier for each pair of different classes.

#### OVR and OVO:
* The OVR and OVO strategies provide a way of combining predictions of binary classifiers.
    - OVR: relatively efficient as train just $k$ classifiers.
    - OVO: $k(k-1)/2$ classifiers, but less data used in each case.
* However a prediction still needs to be made:
    - Basic idea is to use the binary predictions as votes for classes and the class with the most "votes" wins.

#### OVO Example:
Suppose 4 classes: $C_1,C_2,C_3,C_4$ and so for OVO there will be $4 \cdot (4-1)/2 = 6$ classifiers.
<br> 
Using the classifiers to vote:
| | $BC_1$| $BC_2$ | $BC_3$ | $BC_4$ | $BC_5$ | $BC_6$ | Votes |
|:---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|$C_1$| + | - | - | 0 | 0 | 0 | 1 |
|$C_2$| -|0|0|-|-|0|0|
|$C_3$| 0|+|0|+|0|+|3|
|$C_4$| 0|0|+|0|+|-|2|

- Issue arrises if classes get equal votes.
    - If the classifier outputs scores or probabilities:
        - loss-based decoding.
