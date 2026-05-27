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

**Lecture 3** - Multi-Class Classification
- One Versus Rest
- One Versus One
- evaluating cluster performance: with and without ground truth 
- Sub-Group Discovery

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
**Max Depth** $\rightarrow$ $d + 1$ 
**Max n of Leaves** $\rightarrow$ $2^d$

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
- more expencive computationally $\rightarrow$ %O(n^2)% per cluster

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



---------------------------
**Recap**

Tree models -> "_is feature above certain threshold_?" 
Distance-based models -> "_what do your neighbours look like_?"
Linear models -> "_which side of this line/plane are you on_?"
---------------------------