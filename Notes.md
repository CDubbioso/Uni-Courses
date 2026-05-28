**[Part 1](#1-ml-core-ingredients)** - Machine Learning Core Ingredients
- tasks 
- models 
- features

**[Part 2](#2-binary-classification)** - Binary Classification 
- contingency table
- performance metrics 
- evaluation strategies
- Over-fitting, Under-fitting
- Decision Rule, ROC curve

**[Part 3](#3-multi-class-classification)** - Multi-Class Classification
- One Versus Rest
- One Versus One
- evaluating cluster performance: with and without ground truth 
- Sub-Group Discovery

**[Part 4](#4-tree-models)** - Tree Models
- decision trees 
- impurity measures 
    - misclassification 
    - entropy
    - Gini
- purity gain, splitting
- pruning
- sensitivity to skewed class distribution
- regression trees

**[Part 5](#5-distance-based-models)** - Distance-Based Models
- Centroid - Medoid 
- KNN
- K-Mean
- K-Medoid
- Inertia - Silhouette
- Dendrogram 
- Linkage Functions

**[Part 6](#6-linear-models)** - Linear Models
- Least-Square Method
- Linear Regression 
    - RMSA 
    - $R^2$
- Perceptron 
- SVM
- Kernels

**[Part 7](#7-features)** - Featrues
- Calculations on features
- Types of features 
- Feature Transformation 
- **PCA** 

**[Part 8](#8-probabilistic-models)** - Probabilistic Models

**[Part 9](#9-model-ensembles)** - Model Ensembles
- Bootsrapping
- Bagging 
- Subspace Sampling
- Random Forest 
- Boosting 
- Stacking 

- [Significance Testing](#machine-learning-experiments) 
    - t-test
    - Wilcoxon 
    - Friedman
    - post-hoc

**[Part 10](#10-neural-networks)** - Neural Networks 
- non-deep vs deep learning approaches
- Multi Layer Network
- Activation functions
- Gradient Descent
- Back-propagation 
- Efficiency improvement

**[Part 11](#11-xai---explainable-ai)** - xAI 
- White Box vs Black Box
- Categorie xAI 
- LIME 
- Perturbation-based xAI

------
## 1. ML Core Ingredients
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

------
## 2. Binary Classification 
**Binary Classifier** maps an instance to one of two class labels. 
To assess performance of a binary classifier $\rightarrow$ CONTINGENCY TABLE. 
|                | **Predicted Positive** | **Predicted Negative** | *Total* |
|---------------------|---------------------|---------------------|----------|
| **Actual Positive** | True Positive (TP)  | False Negative (FN) | Pos |
| **Actual Negative** | False Positive (FP) | True Negative (TN)  | Neg |
| *Total* | TP + FP | FN + TN | n |

### Evaluate Perofrmance
**Accuracy**  $\rightarrow$  correct predictions across test set

$$\text{accuracy} = \frac{TP + TN}{n}$$

**Recall** - TPR - Sensitivity  $\rightarrow$  positives correctly identified

$$\text{recall} = \frac{TP}{Pos}$$

**Specificity** - TNR  $\rightarrow$  negatives correctly identified

$$\text{specificity} = \frac{TN}{Neg}$$

**Precision**  $\rightarrow$  reliability of positive predictions 

$$\text{precision} = \frac{TP}{TP+FP}$$

**$F_{1}$ Score**  $\rightarrow$  harmonic mean of precision and recall 

$$F_{1} = 2 \times \frac{prec \times rec}{prec + rec}$$ 

$\rightarrow$ $F_1$ not affected by negatives 

---

### Evaluations Strategies
TRAIN-TEST Split 
- divide the data in trainig set (to learn the model) and test set (to evaluate the model).

$\rightarrow$ data can be ordered in some way, therefore mix data before separating the two sets. 

CROSS-VALIDATION 
- repeat train-test split on differnt parts of data. 
- average performance

$\rightarrow$ !!! model might be biased on the dataset used !!! $\Rightarrow$ add ***validation set***. 

TRAIN - VALIDATION - TEST
- Validation set = use different dataset to compare _candidate models_ and pick th ebest one. 
    - candidate models: different algorithms or different hyperparameters

---

### Performance Measures
**Over-fitting**: model performs very well on trainig data but badly on test data. 

**Under-fitting**: model performs badly on both training data and test data. 

---

### Visualising Classification Performance
**Decision Rule - Threshold** 
- classifiers uotput a score
- if score > τ, predict positive, else negative
- changing τ you obtain a different contingency table

**ROC Curve**
Plots sensitivity (true positive rate) versus false positive rate (1-specificity). 
- shows sumary of contingency table for different thresholds. 
- best threshold usong ROC is where the curve is the closest to top left corner. 

**AUC** - Arean Under the Curve
- measures performance of a classifier across all thresholds. 
- if AUC of model 1 is higher that another, it means that model 1 is better at distinguishing between classes
    - AUC = 0.5 $\Rightarrow$ no skill 
    - AUC $\rightarrow$ 1.0 $\Rightarrow$ perfect 
    - AUC $\rightarrow$ 0.0 $\Rightarrow$ bad 

---

### Scoring 
Scoring classifier: outputs scores showing confidence for each class

Margin: line that separates the correct and wrong classificaitons

Loss Function: measure how bad predictions are and guide model training by minimizing loss.

### Ranking
Ranking Error: how often a positive example is scored lower than a negative one. 
- Lower ranking error means better ranking quality. 

--- 

### Class Probability Estimation 
- instead of outputting labels or scores, it estimate probabilities for each class. 

**Mean Squared Error** (MSE): how close predicted probabilities are to true class labels

$$SE(x) = \frac{1}{2} \sum_i (\hat{p}_i(x) - I[c(x)=C_i])^2$$

$$MSE(x) = \frac{1}{|\text{Te}|} \sum_{x \in \text{Te}} SE(x)$$

------
## 3. Multi-Class Classification
Combine multiple binary classifiers. 

How to convert binary classifier into Multi-class classifier?
1. One versus Rest
2. One versus One

**One Verus Rest**: train one classifier per class 
- is the point in my class or in any of the others? 
- number of classifier needed:
    - with ordering $\rightarrow$  $k-1$
    - without ordering $\rightarrow$  $k$ 

**One Versus One**: each clasifier ignores all but two classes
- number of classifiers needed:
    - symmetric $\rightarrow$  $\frac{k(k-1)}{2}$
    - asymmetric $\rightarrow$  $k(k-1)$

### Evaluate Multi-class Classifiers
Confusion Matrix for multi-class

Accuracy:

$$\frac{\sum (\text{diagonal entries})}{tot}$$

Per-class Precision and Recall: 

$$prec_i = \frac{TP_i}{TP-i + FP_i}   \qquad \quad   rec_i = \frac{TP_i}{TP_i + FN_i}$$

Weighted overall precision: 

$$\text{Prec} = \sum_i \text{prec}_i \times \text{proportion}$$

**ROC Curve** for multi-class
$\rightarrow$ compute one ROC per class, then aggregate
- to summarize performance:
    - MACRO-AVERAGE: $\qquad$ $macro-TPR = \frac{TPR_1 + TPR_2 + ... + TPR_n}{n}$
        - sensitive to performance on rare classes
    - MICRO-AVERAGE: $\qquad$ $micro-TPR = \frac{TP_1 + ... + TP_n}{Pos_1 + ... + Pos_n}$
        - reflect class imbalance 

### Regression 
Regression models are evaluated by applying a loss function to the residuals.
- Residual = Actual value − Predicted value
- Loss functions measures how far predictions are from true values (Sum of residuals squared)

Is the linear model performing good?
- it has to have:
    - low error 
    - generalisability

**Bias-Variance Trade-off**
- Bias: Error from wrong assumptions in model.
- Variance: Error from sensitivity to small fluctuations in training set.
- Low bias → complex model 
- low variance → simple model

$\rightarrow$ Goal: balance both for best generalization. 

### Unsupervised and Descriptive Learning
Evaluating Clustering Performance
- With Ground Truth (We know the real groups): Use metrics like 
   - Rand index
   - Precision
   - Recall
   - F1 score.
- Without Ground Truth (No real labels): Use internal metrics like 
   - Davies-Bouldin index
   - Calinski-Harabasz Index
   - Silhouette coefficient
        - $s = \frac{b - a}{\max(a,b)}$
            - close to +1 → good clustering: 
            - close to 0 → borderline;
            - negative → wrong cluster:
        * $a$: average distance to points in the same cluster
        * $b$: average distance to points in the nearest other cluster

**Sub-Group Discovery**
Supervised and Descriptive learning task.
- finds subgroups in the data that are statistically unusual 
    - not just aiming for accuracy 
- Chi-square to see if the subgroup differs significantly. 

------
## 4. Tree Models
- supervised learning
- split data based on rules $\rightarrow$ easy to interpret
- three main types:
    1. Decision Trees, single tree
    2. Random Forest, multiple trees combined
    3. Gradinet Boosting, trees built sequentially to correct errors 

---
### Decision Tree
- tree-like graph:
    - Nodes: pick a feature and ask a quesiton
    - Branches: (sdges) answer the question
    - Leaves: outputs/class label 

with "d" number of binary features: 
- **Max Depth** $\rightarrow$ $d + 1$ 
- **Max n of Leaves** $\rightarrow$ $2^d$

$\Rightarrow$ we want to split data so that each child is as pure as possible 
- two types of splits:
    - **PURE** split, each child has only one class
    - **IMPURE** split, children have mixed class 

Measure Impurity, how mixed the class are in a node
- Misclassification Error: 

$$\text{min}(p, 1-p)$$

- Entropy: measure uncertanty

$$-p \log_2 p - (1-p) \log_2 (1-p)$$

- Gini Index: measure prob. of uncertanty

$$2p(1-p)$$

Comparing Splits Using Impurity

1. calculate weighted impurity for children after the split.
2. choose the split that reduces impurity the most (purity gain):

$$\text{Purity Gain} = \text{Impurity before split} − \text{Weighted impurity after split}$$

3. The split with the ***highest purity gain*** is the best split.

For Handling Continuous Features, we check impurity for each possible threshold and pick the best.

---
**PRUNING** Decision Trees

Trees can become very big to fit the data $\rightarrow$ creates risk of "overfitting" 

To prevent this:
- limit number of iterations
- PRUNING $\rightarrow$ reduce tree size by removing weak branches 

Reduced error pruning 
* Start from leaves, replace a node with majority class label 
* Keep the change only if validation accuracy does not drop

$\rightarrow$ helps the tree generalize better the new data 

$\rightarrow$ pruning will not improve accuracy on training set

**Sensitivity** to Skewed Class Distribution 
When classes are imbalanced, tress might be biased 

Sources of imbalance:
- asymmetric class distribution 
    - one class has simply more examples than the other. 
- asymmetric mis-classification cost
    - the classes might be balanced in count, but getting the rare one wrong matters more. 

Solutions:
- add more samples to minority class
- adjust impurity calculations or splitting criteria to be less sensitive to class imbalance 

The reason this happens with trees specifically: entropy and Gini, the measures used to grow the tree, **react to the overall class proportions**. If you scale up the majority class, the impurity scores shift and the tree starts favoring splits that please the majority. This is also why introduce $\sqrt{\text{Gini}}$​ 

$\sqrt{\text{Gini}}$​ 
- do *not* care about those proportion shifts 
- it's insensitive to changes in class distribution 

---
### Regression Trees
Decision Tree that can also be used when the target is a continuous numerical value. 

$\rightarrow$ instead of class labels, leaf nodes hold mean values of target variable in that subset

Measuring Impurity 
- Use **variance** (average squared difference from mean) instead of class impurity:

$$\text{Var}(Y) = \frac{1}{|Y|} \sum_{y \in Y} (y - \bar{y})^2$$

- Find splits that **reduce variance** the most (variance reduction).

Finding Splits in Regression Trees

* Try different thresholds on each feature.
* Calculate weighted variance after splitting.
* Choose the split with **lowest weighted variance**.

------
## 5. Distance-Based Models
Classify instances by computing distances between these instances and a number of internally stored exemplars. 

$\rightarrow$ compare the new point to the one you've already seen 

EXEMPLARS $\rightarrow$ single point that represent at best a group of points
- **CENTROID** : geometric mean
    - easy to compute 
    - virtual point $\rightarrow$ do not correspond to an actual point
- **MEDOID** : geometric median
    - time cosuming to calculate 
        - you would need to calculate, for each data point, the total distance to all other data points, in order to choose the point that minimises it. 
    - actual point 

Measure Distance $\rightarrow$ **Minkowski** distance

$$Dis_p(x, y) = \left( \sum_{j=1}^d |x_j - y_j|^p \right)^{1/p}$$

* $p$ controls the type of distance.
    * If $p=1$, this is **MANHATTAN distance**.
    * If $p=2$, this is **EUCLIDEAN distance**.
    * As $p \to \infty$, the distance becomes **CHEBYSHEV distance** (For maximum difference along any coordinate).


Changing $p$ lets us adjust how we measure "closeness" between points. Different values of $p$ capture different notions of distance, which can be more suitable for certain data types or problems. 

$\rightarrow$ by choosing the right $p$, we can help the algorithm perform better for the specific data or task at hand.

**Distance Metric** must satisfy: 
- **Zero distance to itself**: $\text{Dis}(x,x)=0$
- **Positive for different points**: $\text{Dis}(x,y) > 0 \text{if} x \neq y$
- **Symmetry**: $\text{Dis}(x,y) = \text{Dis}(y,x)$
- **Triangle inequality:** $Dis(x, z) \leq Dis(x, y) + Dis(y, z)$

if $2^{nd}$ condition allows $0$ even though $x \neq y \rightarrow$ PSEUDO-METRIC 

--- 
### KNN - Nearest-Neighbour Classification
- each training instance acts as an exemplar
- to classify a new point, find the *k-nearest* training points
- take a vote among the k-nearest exemplars $\rightarrow$ class with majority of votes wins

How to choose $k$? 
- small $k$ $\rightarrow$ low bias, high variance, overfitting
- big $k$ $\rightarrow$ high bias, low variance, underfitting

$\rightarrow$ optimal $k$ usually between $0 \leq k \leq 10$
- use cross-validation to find best $k$ 
- weighted voting $\rightarrow$ give more weight to closer neighbours

---
### Distance Based Predictive Clustering
Predictive clustering: use a distance metric to construct exemplars and a distance-based decision rule to create clusters. 

---
### K-Means Algorithm
1. randomly initialize $k$ centroids
2. assign each point to the nearest centroid 
3. update centroids to be the mean of assigned points
4. repeat 2-3 untill no change is centroids 

Limitations:
- sensible to initial centroids
- need to know $k$ beforehand 
- uses Euclidian distance
- computation $\rightarrow$ $O(n)$ per cluster
---
### K-Medoids Algorithm 
$\rightarrow$ same structure of k-mean
- works with any distance metric
- more robust to noise/outliers
- more expencive computationally $\rightarrow$ $O(n^2)$ per cluster

1. Pick K random points as medoids.
2. Assign points to closest medoid.
3. Update medoids to minimize total distance within cluster.
4. Repeat until medoids stabilize.
---
### Evaluating Clustering
- INERTIA: how compact clusters are $\rightarrow$ low inertia = tight cluster

$$\text{Inertia} = \sum_{i}^{n} \min_{\mu_i \in C} \|x_i - \mu_i\|^2$$

- SILHOUETTE: how similar a data point is to its own cluster vs the next closest cluster

$$s(x_i) = \frac{b(x_i) - a(x_i)}{max(a(x_i),b(x_i))}$$

- $\rightarrow$ we want high $b$ and low $a$
    - $a(x_i)$ : average distance of $x_i$ to points in its cluster
    - $b(x_i)$ : average distance of $x_i$ to points in neighbour cluster

    - $s \rightarrow 1$, point in its cluster
    - $s \rightarrow 0$, point near cluster boudary
    - $s$ negative, point is closer to other cluster 

---
### Descriptive Hierarchical Clustering
Build a hierarchy/tree of clusters
- the output is a tree $\rightarrow$ **Dendrogram**:
    - leaves are data points, internal nodes represent merged clusters
    - height at which two groups join shows distance at which cluster merged (how different when they were merged)
---
### Linkage Functions $\rightarrow$ How to measure distance between clusters
* **Single linkage:** minimum distance between points in two clusters.
    - measure from the _two closest members_, one from each group
* **Complete linkage:** maximum distance between points in two clusters.
    - measure from the _two farthest members_
* **Average linkage:** average distance between points in two clusters.
    - average distance over all cross-group pairs 
* **Centroid linkage:** distance between cluster centroids.
    - issue: a merged cluster's centroid can land in a spot that makes earlier sub-clusters effectively "vanish" 
---
### Hierarchical Agglomerative Clustering - HAC
Idea: build tree by gluing things together starting from smallest pieces.
1. start by treating each data point as its own tiny cluster
2. find the two closest clusters, using linkage functions, merge them into one 
3. repeat untill one cluster remains

Result $\rightarrow$ dendrogram that represent cluster hierarchy

- choice of linkage function will affect the result
- sometimes clusters suggested by dendrograms don't match real data
- silhouette scores can help check cluster quality 

------
## 6. Linear Models
Geometric model $\rightarrow$ use lines ans planes to draw boundaries, represent similarities between points

### The Least-Squares Method

--- 

### Linear Regression

Best line is the one that sits _closest_ to all the points at once. 

$\rightarrow$ close = minimize square sum of residual

$$\text{residual} = f(x_i) - \hat{f}(x_i)$$

- given n data points $(x_i, y_i)$ and a model $\hat{f}(x_i) = a + b x_i$ 

$$\text{Square Sum Residual} = \text{SSR or RSS} = \sum_{i=1}^n (y_i - (a + b x_i))^2$$

- since SSR is convex (u shape) $\rightarrow$ the minimum is when partial derivative is $0$ 

**Performance of Regression** 

**Root Mean Squared Error** : how wrong am I on average

$$\mathrm{RMSE} = \sqrt{\frac{1}{n} \sum_{i=1}^n (f(x_i) - \hat{f}(x_i))^2}$$

**$R^2$ - Coefficient of Determination** : is my line actually better that just guessing the average

$$R^2 = 1 - \frac{\mathrm{RSS}}{\mathrm{TSS}}$$

where:
- Residual Sum of Squares, **RSS**:

$$\mathrm{RSS} = \sum_{i=1}^n (f(x_i) - \hat{f}(x_i))^2$$

- Total Sum of Squares, **TSS**: 

$$\mathrm{TSS} = \sum_{i=1}^n (f(x_i) - \bar{f}(x_i))^2$$

$\Rightarrow$ the closer $R^2$ is to $1$, the better the linear regression is. 

--- 

**Effect of Outliers**

Outliers strongly eggect the regression line because of large residual

Solution:
1. train model $\rightarrow$ detect outliers $\rightarrow$ remove outliers $\rightarrow$ re-train 
2. use *Total Least Square* method

--- 

**Regularized Regression** 

With few data points, the model can overfit the training data. 

$\rightarrow$ low error on training, high error on test 

Regularisation adds a penalty on large weights to avoid overfitting.

$$\text"{ERROR} + \lambda \cdot \text{Penalty on Weights}"$$

Where $\lambda$ is a hyperparameter that controls the amount of regularization.
- Low $\lambda$ → model tries harder to fit the data exactly.
- High $\lambda$ → model keeps weights small and simpler, less sensitive to noise.

--- 

### Using Least-Square for Classification

**Linear Models for Classification** 

We can encode two classes as real numbers:

* Positive class: $y^+ = +1$
* Negative class: $y^- = -1$

Train linear regression to predict these labels.

--- 

### The Perceptron 
Linear classifier that will achieve perfect separation on linearly separable data. 
- starts with a random line
- feed it with training points one at the time
    - if point is correctly classified, move on;
    - if point is misclassified, update the line towards fixing that mistake; 
- repeat untill all points are correctly classified. 

$\rightarrow$ if the data can be split by a straight line, the perceptron will find it. 
- issue: it will find the fist line that happen to make zero mistakes, not necessarily the best one. 

$\Rightarrow$ Perceptron = mistake-driven, self-correcting model

---

### SVM - Support Vector Machine
- fixes the perceptron issue $\rightarrow$ which separating line to choose? 

$\rightarrow$ ***separate the classes with the widest possible gap.*** 

$\rightarrow$ **Pick the boundary that maximizes the margin.** $\leftarrow$

**Hard margin** : zero points in the gap $\rightarrow$ perfect classification
- but there can be outliers that sits within this gap, and we don't want the gap to become absurdly narrow $\rightarrow$ use _soft margin_. 

**Soft margin** : tollerate a few points in the gap if it lets a nice wide gap

---

### Kernels
Allow to extend linear classifiers to non-linear problems. 

_If you can't separate the data in its current space, lift it into a higher-dimentional space where you can_. 

------
## 7. Features

### Calculations on feaures
Three main categories:
1. Statistic of Central Tendency
2. Statistic of Dispersion
3. Shape Statistics

**Statistics of central Tendency** $\rightarrow$ mean - median - mode 

**Statistic of Dispersion**
- **Variance** 
- **Standard deviation** 
- **Range:** Difference between max and min.
- **Midrange:** Average of max and min.
- **Percentiles**: 
    - **p-th Percentiles**: $p$ percent of instances fall below the value
    - **Quartiles**: percentiles for $p$ being multiple of $25$
    - **Deciles**: percentiles for $p$ being multiple of $10$
- **Interquartile range:** Difference between $3^rd$ and $1^st$ quartile.

**Shape Statistics** $\rightarrow$ describe shape of data
- SKEWNESS 
- KUTROSIS, measures how sharp or flat the peak is compared to a normal distribution 
    - positive = sharp, negative = flat

--- 

### Kinds of features
- Categorical/Nominal
- Ordinal
- Quantitative
- Boolean

**Structured features** $\rightarrow$ captures complex info 
- can be contructed:
    - prior to the learning model $\rightarrow$ number of possible features grows out of control, very fast
    - during the learning model

--- 

### Feature Transformation 

| From \ To    | Quantitative | Ordinal | Categorical  | Boolean     |
| ------------ | ------------- | ---------- | --------- | ----------- |
| Quantitative | Normalisation, Calibration | Calibration | Calibration | Calibration |
| Ordinal       | Discretisation | Ordering | Ordering | Ordering |
| Categorical   | Discretisation | Unordering   | Grouping     | - |
| Boolean       | Thresholding | Thresholding | Binarisation | - |

- ***Calibration***: Assigns values to categorical data 
    - can wrongly give more importance to some categories 
- ***Thresholding***: Converts numeric/ordinal features into boolean by splitting at a threshold value 
- ***Discretisation***: Converts quantitative features into ordinal 
    - creates bins where each bin is an interval
- ***Normalization***: rescale every feature to comparable range
    - _MIN-MAX_ normalization $\rightarrow$ $\frac{(\text{value} - \text{min})}{(\text{max} - \text{min})}$
    - _z-score_ normalization $\rightarrow$ $\frac{(\text{value} - \mu)}{\sigma}$
        - creates data around mean $0$ and sd $1$ 

--- 

### Feature Cunstruction & Extraction
**Construction** $\rightarrow$ combine or derive features from raw ones using domain knowledge. 

**Extraction** $\rightarrow$ automatic version
- let the data tell you which combinations matter $\rightarrow$ **PCA**

--- 

### PCA - Principal Component Analysis
Goal: take many correlated features and replace them with new "***super-features***" that captures most of the variation 

1. creates new features by combining original features
2. it finds directions (_components_) where the data varies the most 
- **PC1** explains the most variation
- **PC2** explains the next most variation
    - perpendicular to PC1

Process: 
1. find mean of the data
2. center data by subtracting the mean
3. find the first principal component (PC1)
4. find the next principal components (PC2, PC3, ...)
5. eigenvalues measure importance of each component
6. eigenvectors give direction of components
7. decide how many to keep

$\rightarrow$ PCA helps reduce redundancy when features are correlated

------
## 8. Probabilistic Models


------
## 9. Model Ensembles
Idea: combine many models so that individual mistake don't dominate

$$\Large \text{DIVERSITY} + \text{COMBINATION}$$ 

**Bootstrapping**: train-test many times on random samples
- help reduce mistakes caused by one training set

### Bagging 
$\rightarrow$ Bootstrap AGregating 
- Create multiple bootstrap samples from the original data.
- Train separate models (learners) on each sample. (**Bootstrap**)
- Combine their predictions by voting or averaging. (**Aggregate**)

$\rightarrow$ ***reduce variance***

### Subspace Sampling
Instead of using all features, you randomly pick only a small set of features for each model. 
- Different models look at different parts of the data, so their errors won’t be the same. 

$\rightarrow$ helps the combined model ***perform better*** and ***avoid overfitting***

### Random Forest
- Bagging + random feature selection for trees.
- Train many decision trees on different bootstrap samples and random feature subsets.
- Predict by majority vote (classification) or average (regression).

$\rightarrow$ forces tree to be more diverse $\rightarrow$ ***reduce variance*** 

### Boosting
Method for reducing the error in supervised learning by converting weak learners to strong ones. 
- each model learn from the mistakes of the previous one 

$\rightarrow$ ***reduce bias***

### Stacking
- more flexible approach 

$\rightarrow$ you train a second level model (*META-LEARNER*) to learn how best to combine the predictions of multiple base models
1. train $k$ base learners on the data
2. collect their predictions 
3. train a second level learner (meta-learner)

### Bagging Vs Boosting Vs Stacking
| _Bagging_                                 |  _Boosting_                                                  | _Stacking_ |
| ----------------------------------------  | ------------------------------------------------------------ | --------- |
| model train in parallel, are independent  | sequestial → each model learns from mistakes of previous one | base model train in parallel, then a meta-learner on top |
| **reduce variance** | **reduce bias** | **reduce both bias and variance**, depends on model used | 


-----
## Machine Learning Experiments
When algorithm A beats algorithm B in your experiment, is that a real difference or just luck from how the data happened to split $\rightarrow$ use ***Statistical significance testing***

### Significance testing:
- start with a _null hypothesis_ $\rightarrow$ assumption that there is no real difference and any observed gap is due to chance
- compute $p$-_value_ 
- reject if $p < \alpha$, where $\alpha$ is our significance level (typically $0.05$)

---

How many algorithms and how many datasets you're comparing?

### Paired t-test
- ***two algorithms, one dataset*** $\rightarrow$ **paired t-test**
    - use cross-validation
    - compute difference in accuracy on each fold

### Wilcoxon signed-rank test 
- ***two algorithms, multiple datasets*** $\rightarrow$ **Wilcoxon signed-rank test**
    - rank performance differences in absolute value
    - calculate sum of ranks for positive and negative differences separately and take the smaller of these sums as our test statistic. 
    - compare against a critical value from the table
    - Null Hypothesis: the two algorithms perform equally across datasets. 

### Friedman Test
- ***multiple algorithms, multiple datasets*** $\rightarrow$ **Friedman test**
    - rank performance of $k$ algorithms within each data set 
    - average each algorithm's ranks across datasets 
    - Null Hypothesis: all algorithms perform equally $\rightarrow$ all average ranks are equal

### Post-hoc test
**Friedman Test** $\rightarrow$ needs ***post-hoc test*** 
- Friedman only tells you whether there's a significant difference somewhere among the algorithms, not which pairs differ $\rightarrow$ calculte a **Critical Difference** (**CD**) value
    - if difference between the average ranks of two algorithms is greater than CD, their performance difference is significant. 


------
## 10. Neural Networks
**Perceptron** $\rightarrow$ perfectly separate linearly separable classes with a line  

To get ***non-linear boundaries*** you have to bend the space. 

To introduce non-linearities we have to:
1. map our input data 
2. introduce kernels

$\rightarrow$ we do not know a priori what constitutes a good kernel or a meaningful non-linear mapping of our data. 

$\rightarrow$ manually engineering such non-linearities can lead to the **curse of dimensionality**. 

Two approaches:
1. **Non-deep learning approach**: manually engineer $\phi$ or kernel
2. **Deep-learning approach**: learn the $\phi$ or kernel

--- 

### Non-Deep Learning approach
Goal : introduce a transformation $\phi$ that wraps the data into a new space where it becomes linearly separable.
- mechanisms:
    - non-linear function $\phi$ $\rightarrow$ **basis function** 
    - **kernel** (SVM) 

$\rightarrow \phi$ doesn't always garantee the data becomes linearly separable, it makes it more linearly separable in many cases. 

Problem : you have to guess the right $\phi$ in advance. 

--- 

### Deep-Learning approach
The **Neural network way** $\rightarrow$ instead of guessing $\phi$, let the machine learn $\phi$. 

### Multi Layer Network $\rightarrow$ *universal approximators*
- Layer 1 : each neuron detects one simple pattern and reports "how much of that pattern it sees" 
- Layer 2 : take reports and combine them into more complex patterns
- .....
- Output Layer : you built sophisticated concepts out of stacked simple parts 

Stacking linear layers gains you nothing $\rightarrow$ mathematically composing linear functions just give one linear function. 

### Activation Functions 
- small non-linear "kink" (bend) applied after each neuron's weighted sum 
- each kink lets the network bend the space a little
    - stack many kinks and you bend the space into any shape you want/need

$\rightarrow$ with enough neurons in a single hiddel layer you can approximate any function 

examples: 
* ReLU: $g(z) = \max(0, z)$
* Sigmoid: $g(z) = \frac{1}{1+e^{-z}}$
* Tanh: $g(z) = \tanh(z)$

### Neural Nets Training
- weight randomly initializes, so its prediction are garbage
- measure how wrong is it with **Loss Function**
- goal : update weights to minimize loss 

### Gradient Descent
Gradient descent is an optimisation algorithm that is used to update the weights of a neural network to reduce loss. 

_Blindfolded Hiker_ analogy:
- loss = a landscape; position = weights, altitude = loss
- blindfolded in fog → can't see whole map, can only feel slope underfoot
- **gradient** = the slope (steepest downhill direction)
- strategy: feel downhill → take small step → refeel → repeat
- **learning rate** = step size
    - too small → crawls forever
    - too large → overshoots the valley, bounces around
- why not solve directly? NN loss is **non-convex**
    - linear regression = one smooth bowl → solve formula for the bottom
    - NN = bumpy terrain, many valleys (**local minima**) → must descend iteratively
    - starting point (initialization) affects which valley you reach

Steps:
1. Calculate gradient (how loss changes w.r.t. weights).
2. Update weights by a small step (learning rate × gradient).
3. Repeat until loss stops decreasing $\rightarrow$ local minima

### Back-propagation 
Computes the error at the output, then propagates blame backward layer by layer, reusing each layer's computation for the one before it 

To assign blame fairly, you work backwards — first figure out how much the final runner's mistake cost, then trace back how much the runner before them contributed to that mistake, and so on

$\rightarrow$ lets gradient descent know how to update each weight.

### Improving Efficiency
Calculating gradients over the whole dataset (batch gradient descent) is slow.

- Variants to speed up training:
    - **Batch Gradient Descent**: Uses the whole dataset per update.
        - most accurate direction, but very slow (1 step = full pass over data)
    - **Stochastic Gradient Descent** (**SGD**): Updates weights after each training example.
        - fast, many steps, but noisy/zigzag path
        - bonus: noise helps escape bad local minima
    - **Mini-batch Gradient Descent**: Uses small groups (batches) of data per update (common in practice). 
        - balance of accuracy + speed
        - maps well onto GPU parallelism


------
## 11. xAI - Explainable AI
$\rightarrow$ "How easily a human can understand why the model decided what it decided?"

ML models are powerful but silent about their reasoning. xAI fill this gap by connecting the output to the input. 

--- 

### White Box Vs Black Box
**White box** = interpretable model
- ex: decision tree, linear models

**Black box** = non-interpretable model
- ex: neural networks

Explainability vs performance trade-off
- the most accurate models tend to be the least interpretable (black box), while the trasparent one are often weaker. 

--- 

### Categories of Explainable AI Methods
| Category | Description |
| ------------------------- | ------------------------------------- |
| **Post-hoc** | Explain model decisions *after* training (applies to any model, especially black-boxes) |
| **Intrinsic** | Models designed to be interpretable by themselves (white-box models) |
| **Model-specific** | Methods designed for a particular type of model (linear regression coefficients) |
| **Model-agnostic** | Methods that work without needing to know model internals, just input-output behavior (LIME) |
| **Local explainability** | Explain a single prediction for one specific input instance |
| **Global explainability** | Explain the overall behavior of the entire model |

--- 

### LIME 
**LIME** = ***Local Interpretable Model-Agnostic Explanations***

**Local** $\rightarrow$ instead of explaining the entire model, LIME explains one specific prediction by approximating the model in the small region around that instance.

**Interpretable** $\rightarrow$ LIME uses an inherently interpretable model (translator) called **surrogate**
- surrogate goal : mimic the black box behaviour in the local part it selected 
- The surrogate is only locally faithful — a feature important for one instance may be irrelevant globally, and vice versa

**Model-Agnostic** $\rightarrow$ only needs to query inputs-outputs 

### Perturbation-based xAI
Mechanism: 
- break input into interpretable pieces 
- perturb them 
- query the black box 
- weight by proximity 
- fit a weighted linear model 
- read off the weights as feature importances.

LIME minimizes a loss with two terms:

$$\xi(x) = \arg\min_{g} \; \mathcal{L}(f, g, \pi_x) + \Omega(g)$$

where $\mathcal{L}$ rewards local faithfulness and $\Omega(g)$ penalizes complexity (e.g. number of non-zero weights). 
- too simple → low fidelity
- too complex → not interpretable. 

Canonical example: LIME revealed a husky/wolf classifier was actually detecting snow in the background — right answers for the wrong reason

---------------------------
# Recap

Tree models -> "_is feature above certain threshold_?" 
Distance-based models -> "_what do your neighbours look like_?"
Linear models -> "_which side of this line/plane are you on_?"

