# Lecture 2 — Data Collection
*Research Methods in AI · 2025–2026*

> **The big picture.** Lecture 1 was about *thinking* and *evaluating*; this lecture is about *getting the raw material*: data. In AI especially, results are only as good as the data behind them ("garbage in, garbage out"). The lecture walks through four stages of turning the world into usable data: defining **variables & metrics** (what to measure and how), **collecting** them (from which sources), **annotating** them (adding human-provided labels), and packaging the design into a research **proposal**.
>
> *Note: there is no recording transcript for this lecture, so these notes are built from the slides.*

---

## 1. Variables & Metrics

**Intro.** Before collecting anything, you must decide *what* you are measuring and *how* it is represented. A variable is the basic unit of measurement; good variables are unambiguous and complete, which is what makes later inferences valid.

**Key terms**
- **Variable** — anything that can take on a value; in a dataset, usually a *column*. Formally, a function mapping a unit of analysis to a measurement, e.g. `height(Leia) = 150`.
- **Feature (X)** — a predictor variable (input used to predict).
- **Target / Label (Y)** — the variable you want to predict or explain.
- **Quantitative / numerical data** — numerical values (continuous or discrete) allowing arithmetic.
- **Qualitative / categorical data** — labels and ranks. (The overlap of "qualitative" and "categorical" is imperfect — e.g. interview text is qualitative but doesn't fit neat categories.)
- **Exhaustive** — the categories fully cover everything being measured (nothing is left out).
- **Mutually exclusive** — categories don't overlap in meaning or boundaries (every case fits exactly one).
- **Structured (tabular) data** — relationships between components are strictly defined (rows × columns).
- **Unstructured data** — no clear structure on how components relate (text, images); ~80–90% of growth in corporate data.

### Exhaustive vs. mutually exclusive ⭐ *(exam focus)*

These are the two requirements for sound measurement categories. The slide's example: *"How would you categorize programming languages?"*

| Principle | Meaning | Bad version | Fixed version |
|---|---|---|---|
| **Exhaustive** | Every possible case has a home | "Easy / Fast / Popular" (what about a language that's none of these?) | Add **"Other: (specify ___)"** so nothing is uncoverable |
| **Mutually exclusive** | No case fits two categories | "Easy / Fast / Popular" (a language can be all three at once) | "Assign each language to **exactly one** category based on its *main distinguishing characteristic*" |

> **Why it matters:** if categories overlap or leave gaps, responses are ambiguous and the variable can't be interpreted validly — a measurement-side echo of the validity concerns from Lecture 1.

### Quantitative vs. qualitative, structured vs. unstructured

| | Quantitative / numerical | Qualitative / categorical |
|---|---|---|
| **Values** | Numbers (continuous or discrete) | Labels, ranks, text |
| **Operations** | Arithmetic allowed | Counting/grouping |
| **Example** | % correct, daily steps, time-to-task, memory used | Diagnosis, favourite colour, interview answers |

**Supervised example (Titanic, Kaggle):** features could be ticket class, sex, age, # siblings/spouses, fare, port; the **target** is *Survival*.
**Unsupervised example:** the MovieQA dataset — no single label to predict; structure is discovered.

---

## 2. Collection

**Intro.** Once variables are defined, you choose a *source*. Each source measures different things and carries different biases.

**Key terms**
- **Self-report** — data from what people say about themselves (questionnaires, surveys, interviews); used for attitudes, beliefs, emotions, judgments.
- **Questionnaire** — a structured *set of questions* (a **tool**, not a method).
- **Survey** — a *method/strategy* of collecting data from a sample to generalise to a population (broader than a questionnaire; can contain questionnaires and interviews).
- **Interview** — direct interaction, on a continuum from **structured** → **semi-structured** → **unstructured**.
- **Response bias** — a systematic tendency in *how* people answer, independent of content; threatens validity.
- **Social desirability bias** — answering to look good / conform to social norms rather than truthfully.
- **Acquiescence (yea-saying) bias** — tendency to agree regardless of content; **nay-saying** is the opposite.
- **Behavioural observation** — observing and recording actual behaviour.
- **Reactivity** — people changing their behaviour *because* they know they're observed.
- **Archival data** — existing datasets collected previously (records, databases), including **web-scale corpora** (social media, reviews, web text).

### Self-report: tool vs. method vs. technique

| | Questionnaire | Survey | Interview |
|---|---|---|---|
| **What it is** | A set of structured questions (a *tool*) | A *design/strategy* for collecting + generalising | A data-collection *technique* (direct interaction) |
| **Mode** | Written or digital; self- or researcher-administered | Online, mail, face-to-face | Structured / semi-structured / unstructured |
| **Data** | Mostly quantitative (+ open items) | Descriptive, correlational, explanatory | Often qualitative (quantitative if structured) |

**Response formats:** open-ended (rich, not leading, but costly to code), rating scales (easy to process; choose scale length 4/5/7… and labels), multiple choice (choose options + labels).

### Response biases ⭐ *(exam focus)*

| | Social desirability | Acquiescence (yea-saying) / nay-saying |
|---|---|---|
| **What** | Answering to appear favourable / socially acceptable | Tendency to **agree** (or with nay-saying, **disagree**) regardless of the actual question |
| **Example** | Under-reporting socially frowned-on behaviour | Ticking "agree" down a whole scale; LLMs trained on humans even show acquiescence bias (Braun 2025) — Grok's "argumentative mode" disagrees on purpose |
| **Solutions** | Anonymity & confidentiality; indirect questioning; self-administration | Reverse-scoring some items (flip polarity); control questions; neutral language |

> Both biases threaten **validity** (Lecture 1): the measured score reflects the response style, not the construct.

### Behavioural observation ⭐ *(exam focus)*

Behavioural observation is classified along **two independent axes**: *setting* and *concealment*.

| Axis | Options | Meaning | Trade-off |
|---|---|---|---|
| **Setting** | **Naturalistic** | Behaviour as it occurs in real life (participant observation, park usage) | High realism (external validity), less control |
| | **Contrived** | Behaviour in an artificial setting (lab or field experiment) | More control, less realism |
| **Concealment** | **Unconcealed** | Participants know they're observed | → **Reactivity** (behaviour changes) |
| | **Concealed** | Participants unaware / deceived | Avoids reactivity, but **ethical concerns** |

**Solutions for the concealment dilemma:** partial concealment, knowledgeable informants, **unobtrusive measures** (traces that don't disturb behaviour). Example: these axes apply directly to studying user interfaces.

### The four data sources at a glance

| Source | Measures | Examples | Watch out for |
|---|---|---|---|
| **Self-report** | Attitudes, beliefs, emotions | Questionnaires, surveys, interviews | Response biases |
| **Behavioural observation** | Actual behaviour | Smartphone use, parent–child interaction | Reactivity, ethics |
| **Physiological / sensor** | Bodily signals | Heart rate, wearables, EEG, fMRI | Equipment/conditions |
| **Archival** | Pre-existing records | Medical/educational/admin data, web corpora | Provenance, bias |

---

## 3. Annotation

**Intro.** AI models often need human-added context (labels) for the thing being measured. The people who add it are **annotators / coders / raters**. At scale this is done via crowdworking, which is powerful but needs quality control.

**Key terms**
- **Annotator / coder / rater** — a human who labels data to provide context for measurement.
- **Crowdworking** — using online crowd platforms (Amazon Mechanical Turk, Prolific, Appen) to collect labels at scale.
- **Inter-rater reliability** — the degree to which different annotators agree.
- **Gold standard** — items with known correct labels used to check annotator quality (and later, to evaluate models).
- **Annotation aggregation** — combining multiple annotations into one reliable label/score.

### Risks of crowdworking → solutions

| Risk | Solution |
|---|---|
| Low-quality / careless / random labels | **Multiple annotations** per item + **inter-rater reliability** |
| Unclear instructions → inconsistent or systematically wrong labels | **Qualification training** (ensure basic competence) |
| Demographic bias | Diverse pools; **expert review** |
| (Detecting bad workers) | **Gold-standard checks** against known labels |

### Aggregation methods

| Method | How | Best for |
|---|---|---|
| **Majority vote** | Take the label most annotators chose | Categorical labels (object detection, sentiment) |
| **Mean score** | Average the numerical ratings | Continuous scores (sentiment intensity, difficulty) |
| **Confidence-weighted voting** | Weight annotators by reliability/expertise | Reducing influence of low-quality annotators |

> Aggregated scores become a single reference (**gold standard**) for evaluating models. Example: the *Moral Machine* project crowdsourced human judgments on moral decisions for self-driving cars.

---

## 4. Proposal

**Intro.** Weeks 1–2 give you everything needed to write a research proposal. The lecture's checklist for a good one is **SMART**.

**Key term**
- **SMART** — Specific, Measurable, Achievable, Relevant, Time-Bound.

| Letter | Question |
|---|---|
| **S**pecific | Does it narrow down the field of interest? |
| **M**easurable | Are appropriate metrics defined? |
| **A**chievable | Is it feasible (no impossible requirements)? |
| **R**elevant | Do the contributions answer the research question? |
| **T**ime-Bound | Is the planning realistic? |

**Examples (weak → better):**
- *"We will solve climate change by building many nuclear reactors in NL"* → not measurable, not time-bound. **Better:** *"build two reactors and measure the effect on clean-energy supply and global average temperature"* (measurable, time-bound — if slow).
- *"Train a CNN to caption images and see how well it recognises cancer cells"* → not relevant. **Better:** *"train a CNN on a labelled dataset of cancer vs. non-cancer cells, measuring accuracy"* (relevant, measurable).

---

## Final Recap — How It All Connects

This lecture is a pipeline from "the world" to "a dataset you can analyse," and every stage carries a quality risk introduced in Lecture 1:

1. **Variables & Metrics** decide *what* and *how* you measure. Categories must be **exhaustive and mutually exclusive** so the variable is unambiguous — the measurement-level guarantee of validity. Variables split into **features (X)** and **targets (Y)**, and data is **structured** or **unstructured**.

2. **Collection** decides *where* the data comes from — **self-report, behavioural observation, physiological, archival**. Each source has a signature bias: self-report invites **social-desirability** and **acquiescence** biases (→ validity threats), and behavioural observation forces choices about **setting** (naturalistic ↔ contrived, trading external validity for control) and **concealment** (unconcealed → **reactivity**; concealed → ethics). These are exactly the internal/external-validity trade-offs from Lecture 1, now at the data-collection stage.

3. **Annotation** adds the human labels models learn from. Because crowdworkers vary, you protect quality with **multiple annotations, inter-rater reliability, gold standards**, and combine them via **majority vote / mean / confidence-weighted** aggregation — the sampling-and-bias logic of Lecture 1 applied to labels.

4. **Proposal** packages it all. **SMART** is the practical filter that keeps a study specific, measurable, and feasible.

**One-line throughline:** *Define clean variables (exhaustive & mutually exclusive) → collect from a source whose biases you understand (response biases, reactivity) → label reliably (aggregate annotations) → wrap it in a SMART proposal.* Next stop (Lecture 3): rather than collect this data, you'll **simulate** it.
