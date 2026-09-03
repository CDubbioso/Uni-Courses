# Lecture 4 — Data Analysis
*Research Methods in AI · 2025–2026 · Sjoerd Huisman*

> **The big picture.** Now that you have data (real or simulated from Lecture 3), what do you *do* with it? The lecture splits analysis into three goals: **exploratory** (look at patterns, no testing), **confirmatory** (test hypotheses — estimation and p-values), and **prediction** (mostly classification). It reuses the fake chatbot dataset throughout. Two exam-critical ideas live here: the **IQR / quartiles** (exploratory) and **p-values** + **Type I/II errors** (confirmatory).

---

## 1. Three Kinds of Analysis

**Intro.** Not every analysis tests a hypothesis. The lecture organises everything into three buckets (explicitly *not* covering cleaning/preprocessing, text mining, or deep learning).

| Type | Goal | Question it answers |
|---|---|---|
| **Exploratory** | Describe & visualise patterns | "What does the data look like?" |
| **Confirmatory** | Estimate effects & test hypotheses | "Is this pattern real, or just noise?" |
| **Prediction** | Predict a label from features | "Can we guess the outcome for new cases?" |

---

## 2. Exploratory Data Analysis

**Intro.** EDA looks at patterns *without modelling or testing them*: distributions of single variables, relationships between pairs, and broader structure. Looking at your data is essential — it reveals outliers, data-entry errors, and assumption violations, and suggests hypotheses.

**Key terms**
- **Mode** — the most common value (used for categorical variables).
- **Mean** — the arithmetic average.
- **Median** — the value of the middle observation (50% below, 50% above).
- **Five-number summary** — min, Q1, median (Q2), Q3, max (R's `summary()` also adds the mean).
- **Quartile** — cut points dividing ordered data into four equal 25% parts (Q1 = 25th percentile, Q2 = median, Q3 = 75th percentile).
- **Interquartile range (IQR)** — Q3 − Q1: the spread of the *middle 50%* of the data (the box in a boxplot).
- **Outlier (boxplot definition)** — a point more than **1.5 × IQR** beyond the box (Q1 or Q3). *Not* the same as "a wrong value."
- **Variance (s²) / standard deviation (s)** — average squared deviation from the mean / its square root; the most common spread measures.
- **Correlation** — strength of a relationship between two numerical variables (**Pearson** uses values; **Spearman** uses ranks).

### Describing categorical variables
`table(emojis)` (counts), `prop.table()` (proportions), the **mode** (most common value). Plots: **barplot**, **pie** (statisticians often mock pie charts).

### Describing numerical variables — quartiles, IQR & outliers ⭐ *(exam focus)*

`summary(latency)` returns the **five-number summary** + mean. Quartiles split the data into four equal parts:

```
 |---- 25% ----|---- 25% ----|---- 25% ----|---- 25% ----|
min          Q1            Q2=median       Q3           max
             |<--------- IQR (middle 50%) --------->|
```

- The **boxplot** draws this: the box spans Q1→Q3 (so the **box = IQR**), the line inside is the median.
- **Whiskers** extend to the most extreme point *within* 1.5 × IQR of the box.
- Points beyond **1.5 × IQR** are plotted individually as **outliers**.

> **Two cautions from the lecturer:**
> 1. The boxplot "outlier" is a *mechanical* rule (1.5 × IQR), **not** a judgment that the point is wrong — outliers are often just legitimately far from the median.
> 2. But a *huge* gap (e.g. a value of 999 used to code "missing") shows up as an outlier and signals a real data problem.

**Spread also via variance/SD:** `var(latency)`, `sd(latency)`. Histogram (`hist()`) shows distribution *shape* better than a boxplot.

### Relationships between variables

| Pair of variables | Descriptive tool |
|---|---|
| Categorical × categorical | **Cross-table** (`table(emojis, frust_binary)`), grouped barplot |
| Numerical × numerical | **Correlation** + scatterplot (`plot()`) |
| Categorical × numerical | Stats **by group** (`by(...)`), boxplot per group |

**Pearson vs. Spearman correlation:**

| | Pearson (default) | Spearman |
|---|---|---|
| **Uses** | Actual values | Ranks of the values |
| **Captures** | Linear relationship | Monotonic relationship |
| **Robustness** | Sensitive to outliers | **More robust** (outliers lose their leverage once ranked) |

**More than two variables:** use **dimension reduction** (PCA — linear; t-SNE, UMAP — non-linear) or **clustering** (unsupervised classification: hierarchical, k-means).

> ⚠️ **Exploration warning:** if you *test* a hypothesis that you found *by exploring the same data*, you'll find spurious patterns. (Spurious-correlations.com makes the point vividly.)

---

## 3. Confirmatory Analysis (Estimation & Testing)

**Intro.** Confirmatory analysis asks whether the patterns are **real** or just sampling noise. It's **inferential statistics**: using a *sample* to make a statement about a *population*.

**Key terms**
- **Ordinary least squares (OLS) / linear regression** — fits `y = b0 + Σbᵢxᵢ`; in R, `lm()`.
- **Null hypothesis (H₀)** — "nothing going on" (e.g. a coefficient is 0; no effect; no difference).
- **Alternative hypothesis (Hₐ)** — "something is going on."
- **Test statistic** — a number computed from the data (e.g. *t*) used to get a p-value.
- **p-value** — the probability of obtaining this test statistic *or a more extreme one*, **if H₀ is true**.
- **α (alpha)** — the significance threshold (often .05); also the Type I error rate.
- **Type I error** — rejecting H₀ when it is *true* (false alarm; probability α).
- **Type II error** — failing to reject H₀ when it is *false* (missed effect; probability β).
- **Confidence interval** — a range of plausible values for an effect instead of a single point estimate.
- **Frequentist probability** — probability as a long-run *relative frequency*; the truth is fixed, so *hypotheses don't have probabilities*. (This is what p-values assume.)
- **Subjective / Bayesian probability** — probability as a *degree of belief*, updated from prior to posterior; lets you assign probabilities to hypotheses (uses posteriors / Bayes factors, **not** p-values).

### What a p-value really is ⭐ *(exam focus)*

Fit `lm(frustration ~ latency + great_question + response_length + emojis)`; each predictor gets an estimate, a *t* value, and a p-value (stars show significance).

For **latency**, the hypotheses are:
- **H₀:** the latency coefficient = 0 (latency has *no* effect on frustration).
- **Hₐ:** the coefficient ≠ 0.

The p-value answers: *"If latency truly had no effect, how probable is an estimate at least this large?"* If that probability is **low** (< α = .05), we conclude H₀ probably isn't true — something is going on.

> **The crucial misconception** (the lecturer stresses this): the p-value is a probability statement about **the data** (given H₀), **not** about the hypothesis. It does **not** tell you "the probability latency has an effect." Wanting *that* number requires **Bayesian** (subjective) probability — and frequentist statistics *can't* give it, because under frequentism a hypothesis is fixed, not random, so it has no probability.

**Probability — four definitions (quiz):** the "correct" answer is *"it depends,"* but **frequentist** statistics (all p-values, confidence intervals) uses definition **B — a relative frequency over time**. Calculating the probability of a *hypothesis* requires definition **C — degree of belief** (Bayesian).

### Type I vs. Type II error ⭐ *(exam focus)*

| | Reality: H₀ true | Reality: H₀ false |
|---|---|---|
| **Decision: reject H₀** | **Type I error** (prob. α) — false alarm | ✔ correct |
| **Decision: keep H₀** | ✔ correct | **Type II error** (prob. β) — missed effect |

So a **Type I error = "H₀ is rejected while H₀ is true."** Note α is *both* the threshold *and* the Type I error rate.

### Estimation: don't just report point estimates
Because there's uncertainty, report **confidence intervals** (`confint()`) instead of single coefficients. A useful check: the value **0** is excluded from every interval here → every predictor has a statistically detectable effect.

### Other confirmatory models (same logic, different outcome)

| Test | When | R |
|---|---|---|
| **Linear regression** | Numerical outcome | `lm()` |
| **Logistic regression** | Binary outcome (models probability) | `glm(..., family="binomial")` |
| **Chi-squared test** | Two categorical variables (cross-table) | `chisq.test()` |
| **Independent t-test** | Compare a numeric mean across two groups | `t.test(y ~ group)` |

> The **chi-square test** is what the assignment's binary-frustration analysis uses (categorical × categorical from `rbinom()`-style data).

---

## 4. Prediction (mostly classification)

**Intro.** Can we *predict* the label (frustrated yes/no) from the features? Inference models (like logistic regression) can also predict; other models are prediction-only and often **black boxes**.

**Key terms**
- **Confusion matrix** — table of predicted vs. actual classes.
- **Accuracy** — (correct predictions) / (total) = sum of the diagonal / total.
- **Overfitting** — a model so complex it fits the *training* data (even noise) but generalises poorly to *new* data.

**Logistic regression as a classifier:** `predict(..., type="response")` gives probabilities; threshold at 0.5 → classes; build a **confusion matrix** and compute **accuracy** (`sum(diag(m))/sum(m)` ≈ 0.89 here).

**Other classifiers** (assumed familiar from the ML course): **random forest**, **k-nearest neighbours (kNN)**, **neural net** — more black-box (hard to say *why* a prediction is made).

**Overfitting via kNN:** with **k = 1** every point is its own neighbour → 100% training accuracy but a wildly complex boundary that won't generalise. Smaller k = more complex model = better training fit, not necessarily better test fit.

| Concept | Simpler model | More complex model |
|---|---|---|
| kNN | Large k (smooth boundary) | Small k (jagged boundary) |
| Training fit | Lower | Higher |
| Test fit (generalisation) | Often better | Often worse (**overfitting**) |

*(Related ML topics assumed known: sensitivity/specificity, F1 & class imbalance, train/validation/test splits, cross-validation.)*

---

## Exam-style checkpoint (from the lecture quizzes)

1. **What is a Type I error?** → **A. H₀ is rejected while H₀ is true.**
2. **The p-value is a probability statement about…** → **C. the data** (given H₀ — *not* the hypothesis).
3. **If H₀ is true, what does the distribution of the p-value look like?** → **Uniform** (flat) on [0, 1] — every p-value is equally likely under the null.

---

## Final Recap — How It All Connects

The three analysis types form a natural progression on the same chatbot data:

1. **Exploratory analysis** *describes* without testing. For one variable you summarise centre (**mean/median/mode**) and spread (**range, IQR, variance/SD**); the **five-number summary** and **boxplot** make the **quartiles** and **IQR** visible, with the **1.5 × IQR** rule flagging outliers (mechanically, not as "errors"). For pairs you use cross-tables, group summaries, and **correlation** (**Pearson** on values, **Spearman** on ranks for robustness). But exploring and then testing the *same* data invites spurious findings.

2. **Confirmatory analysis** asks whether those patterns are real, via **inferential statistics**. You assume **H₀** ("nothing going on"), compute a test statistic, and get a **p-value** = P(data this extreme | H₀). Low p (< **α**) → reject H₀. The deep point: the p-value describes **the data, not the hypothesis** — assigning probability to a hypothesis needs **Bayesian** (subjective) probability, while p-values are **frequentist** (relative-frequency). Decisions risk **Type I** (false alarm, rate α) and **Type II** (missed effect) errors; report **confidence intervals**, not just point estimates. Different outcomes call for `lm`, `glm` (logistic), **chi-square**, or **t-test** — same logic throughout.

3. **Prediction** turns features into a label. Even inference models predict; you score them with a **confusion matrix** and **accuracy**, and guard against **overfitting** (k = 1 kNN memorises the training set).

**One-line throughline:** *Look first (EDA: quartiles, IQR, correlations) → then test carefully (p-values about the data, Type I/II errors, CIs) → then predict and validate (accuracy, beware overfitting).* Next (Lecture 5): can anyone else **reproduce or replicate** what you found?
