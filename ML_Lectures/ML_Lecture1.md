## Lecture 1 - Machine Learning

Three main ingrediants to machine learning are:
* **Tasks** - problems that require a mapping from data to desired outputs (insights).
* **Features** - characteristics of the data used to describe domain objects.
* **Models** - encode the required task mapping.

### (Some) **Machine Learning tasks - health data as an example**:
* **Classification** 
    - Binary (C=2) classification involves separating data into two distinct groups (+ and -). 
    <br> e.g. distinguishing people at risk from heart disease (+), from those not at risk (-).
    - Generalise to C > 2 different classes.

* **Regression** 
    - Involves mapping from data items to real values. <br> e.g. quantifying the risk of heart disease on the basis of personal health records.

* **Clustering**
    - Separating data into different clusters/concepts on the basis of their characteristics. <br> e.g. grouping people according to their genetic characteristics.

* **Collaborative Filtering** 
    - Identifying rules or associations from data <br> e.g. "recommending" diseases on the basis of patient records and diseases of similar patients.

* **Dimensionality Reduction** 
    - Visualising the data

### Teaching the model:

**Supervised Learning** 
 - Each element of the training data has associated labels. They give the appropriate "output" for the data example. 
- Model generalises from training data 

**Unsupervised Learning** 
- Does not require labels.
- Learns structures and patterns based on similarities and differences in the data features for the training examples.

#### Teaching your models - Degrees of Supervision:
- Not always full/no supervison.
- Semi-supervised machine learning methods use labels on a <u>subset</u> of the data. (particularly relevent when lables are expensive)


### Data and Features:
* Features are the inputs to machine learning:
    - used to describe data objects.
    - represent particular characteristics of an instance.
    - maybe numerical, boolean or nominal.
* A model is only as good as its features. 
    - Thus choice of features is important.
    - Techniques for removing redundant features / transforming features are crucial.


<br>

Course Material:
* Source Material:

    * C. M. Bishop, Pattern Recognition and Machine Learning,Springer, 2007

    * [S. J. D. Prince.  Computer Vision:  Models, Learning, andInference.  Cambridge University Press.  2012](http://web4.cs.ucl.ac.uk/staff/s.prince/book/book.pdf "This book takes a machine learning view on computer vision.")

    * [D. MacKay, Information Theory, Inference and LearningAlgorithms, 2003](http://www.inference.org.uk/mackay/itila/book.html)

* Video Material:

    * [Coursera - Machine Learning](https://www.coursera.org/course/ml) 
    
    * http://videolectures.net → search for “machine learning summer school”
