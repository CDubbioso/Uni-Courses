# Lecture 3 — Data Simulation
*Research Methods in AI · 2025–2026 · Sjoerd Huisman*

> **The big picture.** Instead of *collecting* data (Lecture 2), this lecture *makes it up* — deliberately, transparently, in R. Simulation means drawing values from **distributions** and then wiring in **relationships** between variables so the fake data behaves like real data. The running example builds a fake **chatbot dataset** (150 conversations) variable by variable, ending with a user's **frustration** score that *depends on* the other variables. The course assignment uses exactly this: you simulate data so you have something to test/analyse without spending weeks collecting it.

---

## 1. Why Simulate Data?

**Intro.** Some research questions aren't about the world ("does ice cream cause shark attacks?") but about *methods* ("what's my test's error rate?"). For method questions you don't collect new data — you use benchmarks or **synthetic data** where you *know the truth*.

**Key terms**
- **Inferential statistics** — inferring something about a *population* from a *sample*.
- **Methodological question** — a question about a model/method/algorithm itself (its error rate, robustness to outliers), not about the world.
- **Benchmark** — a commonly-used dataset (MNIST, iris) for comparing methods.
- **Synthetic / simulated data** — data you generate yourself; you know the true labels, so you can measure how well a method recovers them.

**Reasons to simulate** (and one not to):

| Reason | Why it helps |
|---|---|
| Evaluate / compare methods | You *know the truth*, so you can score models fairly (often the proposing paper's method "wins"…) |
| Test an analysis plan | "Fake pilot data" lets you rehearse the analysis before real data exists |
| Education / illustration | Building data teaches you what variables *are* |
| ~~Commit fraud~~ | **Don't.** Simulating is fine *if you say you simulated it* — then it isn't fraud |

---

## 2. R and RStudio (briefly)

**Intro.** R is the tool for the simulation. You don't need deep R, just enough to draw values and combine variables.

**Key facts**
- **R** — interpreted, open-source statistical programming language; popular with statisticians; often *first* to get new statistical methods. Run line-by-line in the console.
- **RStudio** — the IDE (four panes: script, environment, console, plots/help); integrates LaTeX/Markdown; supports reproducible research.
- Assignment `<-` makes objects: `my_object <- 48`. Works on vectors too.
- **`data.frame`** — combines variables (columns of possibly different types) into one object.

---

## 3. Variables and Their Types ⭐ *(exam focus)*

**Intro.** A **variable** is a column / feature — something with observations. A **random variable** is a variable whose values arise from a random process (usually sampling), each value having a probability described by a **distribution**. Variables come in four *measurement levels*, which determine what operations are meaningful.

**Key terms**
- **Random variable** — a variable that takes values via a random process; values have probabilities (a distribution).
- **Nominal** — unordered categories.
- **Ordinal** — ordered categories (`<`/`>` meaningful, but gaps not).
- **Interval** — numbers with *no meaningful zero* (`+`/`−` meaningful, not `×`/`÷`).
- **Ratio** — numbers with a *meaningful zero* (all arithmetic meaningful).
- **Discrete** — a limited (countable) number of possible outcomes.
- **Continuous** — infinitely many possible outcomes.

### The four measurement levels ⭐

| Level | Categorical/Numerical | Meaningful operations | Example (chatbot data) |
|---|---|---|---|
| **Nominal** | Categorical | =, ≠ (groups only) | Emojis used? (no/yes); favourite colour |
| **Ordinal** | Categorical | + order (<, >) | Disease status (healthy/mild/severe) |
| **Interval** | Numerical | + (−) but no meaningful 0 | Temperature (°C/°F); IQ score |
| **Ratio** | Numerical | + (×, ÷); meaningful 0 | **Latency** (s), response length (words), # "Great question!" |

> **Latency** ⭐ is a textbook **ratio** variable: 0 seconds means *no time*, and "twice as slow" is meaningful.

### Discrete vs. continuous

| | Discrete | Continuous |
|---|---|---|
| **Outcomes** | Countable, limited | Infinite |
| **Example** | Number of words; # "Great question!" | Latency in seconds |
| **Caveat** | — | Height is continuous but often recorded as integer cm — so the *recorded* values can look discrete |

---

## 4. Sampling from Distributions

**Intro.** Simulation = drawing random values from a distribution. R's random-draw functions start with `r…`. The shape of randomness differs for discrete vs. continuous variables.

**Key terms**
- **Probability mass function (pmf)** — for *discrete* distributions: vertical lines whose heights are probabilities (sum to 1).
- **Probability density function (pdf)** — for *continuous* distributions: a curve over an interval; probability = *area* under it (any single value has probability 0).
- **`set.seed()`** — fixes the random-number generator so results are *reproducible* (crucial — see Lecture 5).

### Distribution → R function (building the chatbot data)

| Variable | Distribution | R code | Why |
|---|---|---|---|
| Response length | Discrete uniform | `sample(30:200, n, replace=TRUE)` | Equal-probability whole numbers in a range |
| (comparison) | Continuous uniform | `runif(n, min=0, max=10)` | Any real value in a range |
| Latency | Normal (Gaussian) | `rnorm(n, mean=2, sd=0.6)` | Bell-shaped around a mean |
| # "Great question!" | Poisson | `rpois(n, lambda=5)` | Count data |

**pmf vs. pdf in one line:** discrete uniform puts a *spike* of equal height on each integer (heights sum to 1); continuous uniform spreads a flat *density* over the interval (area sums to 1, individual points have probability 0).

---

## 5. Adding Relationships: the Linear Model

**Intro.** Drawing each variable independently is "boring" — variables would be uncorrelated. To make **frustration** depend on the others, the lecture uses a **linear equation**.

**Key terms**
- **Linear model** — `y = b0 + b1·x1 + b2·x2 + … + ε`: an intercept plus weighted predictors plus noise.
- **Noise / error / residual (ε)** — the "unexplained variation"; here `rnorm(n, 0, 2)`.
- **Indicator (dummy) coding** — turning a category into 0/1 so it fits the equation: `(emojis == "yes")` is `TRUE/FALSE`, usable as 1/0.

**Building frustration step by step:**
1. Depend on latency: `frustration <- -2 + 3*latency` → too clean.
2. Add noise: `+ noise` → realistic scatter (the noise = residuals).
3. Add more predictors: `+ 0.1*great_question - 0.01*response_length`.
4. Add the categorical predictor via an indicator: `+ 2*(emojis == "yes")`.

Final model: **y = −2 + 3·x_latency + 0.1·x_greatq − 0.01·x_length + 2·I(emojis = "yes") + ε**

> The *sign and size* of each weight encode the relationship: latency strongly increases frustration (+3); emojis add a fixed +2; longer responses slightly *decrease* it (−0.01).

---

## 6. Recoding and Transformation

**Intro.** Simulated values often fall outside the range you wanted. You fix them by recoding/transforming.

**Key examples**
- **Clamp to a range + round to integers** (frustration should be 0–10 integers):
  `frustration <- round(pmax(pmin(frustration, 10), 0))` — `pmin` caps at 10, `pmax` floors at 0, `round` makes integers.
- **Create skew:** squaring a roughly-normal variable (`x_sq <- x^2`) stretches the upper tail → a right-skewed distribution.

---

## 7. A Binary Outcome: the Logistic Model

**Intro.** What if the outcome is categorical — *"Are you frustrated? (yes/no)"*? Two approaches: threshold a numeric variable, or model a *probability* with a logistic link.

**Key terms**
- **Threshold approach** — turn a number into yes/no by cutting it: `frust_binary <- c("no","yes")[(frustration > 5) + 1]`.
- **Logistic model** — models the *probability* π of "yes": `π = 1 / (1 + e^−(b0 + b1x1 + …))`. The sigmoid squashes the linear predictor from (−∞, ∞) into (0, 1).
- **Log-odds (logit)** — rewriting the above: `log(π / (1−π)) = b0 + b1x1 + …` — a *linear* model for the log-odds.
- **Linear predictor** — the `b0 + b1x1 + …` part fed into the sigmoid (here, no noise term).

**How the linear predictor controls the probabilities:**

| Change | Effect on probabilities |
|---|---|
| Higher **intercept** (e.g. −6.5 → −5.5) | Higher mean probability overall |
| Lower intercept (−6.5 → −7.5) | Lower mean probability |
| Stronger **weights** | More *extreme* probabilities (wider range of the linear predictor) |

**From probabilities to a binary outcome:** sample yes/no using each row's probability —
`sample(c("no","yes"), 1, prob = c(1 - p, p))`.

### Linear vs. logistic simulation

| | Linear model | Logistic model |
|---|---|---|
| **Outcome** | Numeric (e.g. 0–10) | Binary (yes/no) |
| **What's modelled** | y directly | Probability π of "yes" |
| **Noise** | Explicit `ε` term | Randomness enters via sampling yes/no from π |
| **Link** | Identity | Sigmoid `1/(1+e^−x)` |

> **Important:** simulating data *with* a linear/logistic equation does **not** force you to *analyse* it with that model. The same simulated data can feed a t-test, a chi-square test, or a classifier (Lecture 4).

---

## 8. Practical Advice for Simulation ⭐

- **Start simple:** make each variable separately first.
- **Then add relationships** (linear/logistic equations).
- **Then make values realistic** (rounding, clamping ranges).
- **Simulate only what you need:** you usually don't need raw chat logs — simulate the *already-processed* variables your test/classifier consumes.
- Make sure your **research question can be answered** by a statistical test or classifier on the variables you simulate.

---

## Final Recap — How It All Connects

The lecture is one worked example — building a fake chatbot dataset — that teaches the whole logic of simulation:

1. **Why:** for *methodological* questions you want data where you **know the truth**, so you use **benchmarks** or **synthetic data**. Stating that data is simulated is what keeps it honest.

2. **What variables look like:** every column is a **random variable** drawn from a **distribution**, and its **measurement level** (nominal / ordinal / interval / **ratio** — like **latency**) and discrete/continuous nature dictate which **R draw function** to use (`sample`, `runif`, `rnorm`, `rpois`) and whether its distribution is a **pmf** or a **pdf**. `set.seed()` makes it all reproducible.

3. **Relationships:** independent draws are boring, so a **linear model** (`y = b0 + Σ bᵢxᵢ + ε`) wires predictors into the outcome, with **noise** as the residual and **indicator coding** for categories.

4. **Realism & other shapes:** **recoding/transformation** (clamp, round, square-for-skew) fixes unrealistic values, and a **logistic model** produces a **binary** outcome by modelling a *probability* and sampling yes/no from it.

**One-line throughline:** *Draw each variable from the right distribution → tie them together with a linear (or logistic) equation + noise → reshape to realistic values → and remember you can analyse the result with whatever test or classifier your question needs.* Next (Lecture 4): how to actually analyse this data — descriptives, p-values, and classifiers.
