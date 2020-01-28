## Lecture 2 - Machine Learning

Three main ingrediants to machine learning are:
* **Tasks** - problems that require a mapping from data to desired outputs (insights).
* **Features** - characteristics of the data used to describe domain objects.
* **Models** - encode the required task mapping.

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
