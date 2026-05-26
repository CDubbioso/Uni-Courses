**Lecture 1** - Machine Learning Core Ingredients
- tasks 
- models 
- features

**Lecture 2** - Binary Classification 
- contingency table
- performance metrics 
- evaluation strategies
- Over-fitting, Under-fitting
- Decision Rule, ROC curve
- 

## ML Core Ingredients
### Tasks 
Tasks can be "Predictive" or "Descriptive", and "Supervised" or "Unsupervised". 
- Predictive $\rightarrow$ return a function that aims to predict an output given an input. 
- Descriptive $\rightarrow$ aims to find patterns in the data. 
- Supervised $\rightarrow$ we know both input and output. 
- Unsupervised $\rightarrow$ we only know the input.

|               | ***Predictive*** | ***Descriptive*** |
|---------------------|---------------------|---------------------|
| ***Supervised*** | Classification, Regression | Subgroup discovery |
| ***Unsupervised*** | Predictive Clustering | Descriptive clustering, Association rule discovery |

### Models 
What is being learned from the data in order to solve a task.
- Model Categorization by Intuition 
    - **Geometric Models** $\rightarrow$ uses distance, hyperplanes. 
        - ex: Linear Regression, SVM
    - **Probabilistic Models** $\rightarrow$ use probability sistribution to reduce uncertanty. 
        - ex: Naive Bayes
    - **Locical Models** $\rightarrow$ use rules for decision-making. 
        - ex:Decision Trees

- Model Categorization by Modus Operandi (mode of operation) 
    - **Grouping Models** $\rightarrow$ divide instance space into finite number of segments, and learn a simple model per segment. 
        - ex: Decision Trees 
    - **Grading Models** $\rightarrow$ learn a single global function over all instances. 
        - ex: SVM, Linear Regression 

|                | ***Geometric***  | ***Probabilistic***  | ***Logical***  |
|----------------|----------------|--------------|--------------|
| ***Grouping*** | K-means, K-NN  | Naive Bayes  | Decision Trees  |
| ***Grading***  | Linear Regression, SVM, Perceptron | Logic Regression | rare |

### Features 
Measurement that you can perform on any instance. 
- Feature Engeneering: 
    - Feature Construction $\rightarrow$ Creating features from raw data.
    - Discretization $\rightarrow$ Converting numerical data into categorical bins.
    - Feature Transformation $\rightarrow$ Mapping data into a new space (e.g., PCA).
    - Feature Selection $\rightarrow$ Removing redundant or irrelevant features.


## Binary Classification 
**Binary Classifier** maps an instance to one of two class labels. 
To assess performance of a binary classifier $\rightarrow$ CONTINGENCY TABLE. 
|                | **Predicted Positive** | **Predicted Negative** | *Total* |
|---------------------|---------------------|---------------------|----------|
| **Actual Positive** | True Positive (TP)  | False Negative (FN) | Pos |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  | Neg |
| *Total* | TP + FP | FN + TN | n |

### Evaluate Perofrmance
**Accuracy**  $\rightarrow$  correct predictions across test set
> $acc = \frac{TP + TN}{n}$
**Recall** - TPR  $\rightarrow$  positives correctly identified
> $rec = \frac{TP}{Pos} $
**Specificity** - TNR  $\rightarrow$  negatives correctly identified
> $spec = \frac{TN}{Neg} $
**Precision**  $\rightarrow$  reliability of positive predictions 
> $prec = \frac{TP}{TP+FP} $
**$F_{1}$ Score**  $\rightarrow$  harmonic mean of precision and recall 
> $ F_{1} = 2 \times \frac{prec \times rec}{prec + rec}$ 
> $\rightarrow$ not affected by negatives 

### Evaluations Strategies
TRAIN-TEST Split 
- divide the data in trainig set (to learn the model) and test set (to evaluate the model).
$\rightarrow$ data can be ordered in some way, therefore mix data before separating the two sets. 

CROSS-VALIDATION 
- repeat train-test split on differnt parts of data. 
- average performance
$\rightarrow$ !!! model might be biased on the dataset used!!! $\Rightarrow$ add ***validation set***. 

TRAIN - VALIDATION - TEST
- Validation set = use different dataset to compare _candidate models_ and pick th ebest one. 
    - candidate models: different algorithms or different hyperparameters

### Performance Measures
**Over-fitting**: model performs very well on trainig data but badly on test data. 
**Under-fitting**: model performs badly on both training data and test data. 

### Visualising Classification Performance
**Decision Rule - Threshold** 
