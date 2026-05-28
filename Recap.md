---------------------------
# Recap

### The Core Question Each Model Asks
Tree models -> "_is feature above certain threshold_?" 
Distance-based models -> "_what do your neighbours look like_?" 
Linear models -> "_which side of this line/plane are you on_?" 
Probabilistic models -> "_how likely is each class given the evidence_?" 

---

### Setting Up the Problem
**Tasks** -> are we *predicting* an output or *describing* hidden structure? do we have labels (*supervised*) or not (*unsupervised*)? 
**Models** -> geometric (distances/planes), probabilistic (likelihoods), or logical (rules); and within those, *grouping* (split space into segments) vs *grading* (one global function). 
**Features** -> the measurements you feed in; you can construct, transform, discretise, or select them to help the model.

---

### Telling If a Model Is Any Good
**Binary classification** -> everything starts from the contingency table; *recall* asks "did I catch the positives?", *precision* asks "when I said positive, was I right?", and $F_1$ balances the two while ignoring the negatives. 
**Threshold & ROC** -> a classifier outputs a *score*, and sliding the threshold τ traces out the ROC curve; AUC summarises how well it separates classes across *all* thresholds (0.5 = coin flip, 1.0 = perfect). 
**Multi-class** -> just stitch binary classifiers together (one-vs-rest or one-vs-one), then aggregate with *macro* (treats every class equally, kind to rare ones) or *micro* (treats every instance equally, reflects imbalance) averaging. 
**Regression** -> judge by the *residuals*; RMSE says "how wrong on average", $R^2$ says "am I beating just guessing the mean?". 

---

### The One Tension Behind Everything: Bias vs Variance
**Bias** = wrong *assumptions*, model too simple to capture the pattern (underfitting). 
**Variance** = too *sensitive* to the exact training data, fits the noise (overfitting). 
A squiggly boundary that nails every training point = low bias, high variance. The goal is the *sweet spot* that minimises total error, not either extreme.

---

### How the Main Models Actually Work
**Trees** -> greedily split on whichever feature gives the biggest *purity gain* (entropy/Gini drop); prune afterwards so the tree generalises instead of memorising. 
**Distance-based** -> represent groups by *exemplars* (centroid = mean, medoid = real point), measure closeness with Minkowski distance, and let neighbours vote (KNN) or cluster (K-Means/K-Medoids). 
**Clustering quality** -> *silhouette* checks whether points sit comfortably in their own cluster ($a$ small) vs the nearest other one ($b$ large). 
**Linear models** -> fit by *least squares* (minimise squared residuals); the *perceptron* finds *any* separating line, the *SVM* finds the *best* one by maximising the margin. 
**Kernels** -> if you can't separate the data here, lift it into a higher-dimensional space where you can — without ever computing that space explicitly.

---

### Squeezing Out More Performance: Ensembles
**Bagging** -> train models in *parallel* on bootstrap samples, average them -> kills **variance** (Random Forest = bagging + random features). 
**Boosting** -> train *sequentially*, each model fixing the last one's mistakes -> kills **bias**. 
**Stacking** -> let a *meta-learner* figure out how to best combine several base models. 

---

### When Linear Isn't Enough: Neural Networks
Stacking linear layers gains nothing — you need *activation functions* to bend the space. Each neuron adds a small non-linear kink; stack enough of them and you can approximate *any* function. Train by *gradient descent* (walk downhill on the loss surface), using *back-propagation* to fairly assign blame to each weight.

---

### Trusting the Result
**xAI** -> the most accurate models (neural nets) are the least interpretable (*black box*); xAI reconnects output to input. *LIME* explains a *single* prediction by fitting a simple, interpretable surrogate in the local neighbourhood — catching cases like the husky classifier that was really just detecting snow.

---

### Was the Improvement Real, or Just Luck?
Compare algorithms with *significance tests*: paired *t-test* (two algorithms, one dataset), *Wilcoxon* (two, many datasets), *Friedman* + post-hoc (many algorithms, many datasets). Reject the null only if $p < \alpha$ (usually 0.05).