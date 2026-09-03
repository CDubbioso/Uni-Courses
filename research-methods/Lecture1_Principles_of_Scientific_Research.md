# Lecture 1 — Principles of Scientific Research
*Research Methods in AI · 2025–2026*

> **The big picture.** This lecture is about becoming a *critical consumer and producer* of research. It moves through four building blocks that stack on top of each other: how to **think** like a scientist (avoiding the mental shortcuts that fool us), the **process** scientists use to turn observations into tested knowledge (the empirical cycle), the **quality checks** that tell us whether a study's claims can be trusted (validity), and finally a current, AI-specific issue: how **generative AI** is creeping into research and how it should be handled.

---

## 1. Scientific Thinking

**Intro.** Before any method, scientists need a particular *mindset*. Humans are wired with mental shortcuts (heuristics) that usually work fine in daily life but systematically mislead us when evaluating evidence. "Thinking like a scientist" largely means recognising these traps in yourself and in research you read. The lecture demonstrated three of them with live audience problems.

**Key terms**
- **Heuristic** — a fast, intuitive mental shortcut for making judgements; efficient, but error-prone.
- **Bias** — a *systematic* (non-random) deviation from correct reasoning that pushes conclusions in a predictable direction.
- **Confirmation bias** — the tendency to seek, notice, and remember evidence that *confirms* what we already believe, while neglecting evidence that could *disprove* it.
- **Availability heuristic** — judging how likely or frequent something is by how *easily examples come to mind*.
- **Representativeness heuristic** — judging probability by how well something *matches a stereotype*, while ignoring how common it actually is.
- **Base rate** — the underlying overall frequency of something in the population (e.g. how many cashiers vs. librarians exist in total).
- **Hindsight bias** — the "I-knew-it-all-along" effect: after an outcome is known, we believe we could have predicted it.

### The three demonstrations

**Problem 1 — The card task (confirmation bias).**
Rule: *"If a card has a vowel on one side, then it has an even number on the other side."* Four cards are shown: **E**, **K**, **2**, **3**. Which must you flip to test the rule?
- **E** ✔ — it's a vowel, so flip it to check there's an even number behind it.
- **3** ✔ — it's *odd*; if a vowel is behind it, the rule is **broken**. This card can *falsify* the rule.
- **K** ✗ — a consonant; the rule says nothing about consonants.
- **2** ✗ — it's even, but the rule never claims "even ⟹ vowel", so nothing behind it can break the rule.

> **Why it matters:** Most people flip **E** (and often **2**) — they look for *confirmation*. Far fewer flip **3**, the card that could actually *disprove* the rule. That neglect of disconfirming evidence is **confirmation bias**.

**Problem 2 — The letter "R" (availability heuristic).**
Are there more English words *starting* with "r", or more with "r" in the *third* position (e.g. ca**r**e, hea**r**t)? Correct answer: **third position**. But words starting with "r" (ring, roll, run…) are *easier to generate*, so that ease gets misread as higher frequency → **availability heuristic**.

**Problem 3 — Arthur the librarian (representativeness heuristic + base rates).**
Arthur is shy, orderly, perfectionistic. Librarian or cashier? Most say **librarian** because the traits *match the stereotype*. But there are **vastly more cashiers** than librarians, so once you weigh the **base rate**, *cashier* is the more probable answer → **representativeness heuristic** (ignoring base rates).

> **Connecting back:** Problem 1 (confirmation bias), Problem 2 (availability), and Problem 3 (representativeness) are not isolated puzzles — they are three faces of the same lesson: intuition is systematically biased, so science needs deliberate safeguards.

### Comparison table — the three core biases/heuristics

| Bias / Heuristic | What it is | Triggered in the lecture by | Tell-tale error | Scientific antidote |
|---|---|---|---|---|
| **Confirmation bias** | Seeking/recalling confirming evidence | Card task (E, K, 2, 3) | Not looking for the case that could *disprove* you (the "3" card) | Actively try to **falsify** your hypothesis |
| **Availability heuristic** | Frequency judged by ease of recall | Letter "r" question | Vivid/easy examples feel more common (e.g. plane vs. car crashes) | Check **actual frequencies / data** |
| **Representativeness heuristic** | Probability judged by stereotype fit | Arthur (librarian vs. cashier) | Ignoring how common each option really is | Weigh the **base rate** |

> **Feynman's principle (the lecture's anchor quote):** *"The first principle is that you must not fool yourself — and you are the easiest person to fool."* Even people who *know* these biases still fall for them; the goal is to build habits that catch them.

---

## 2. The Empirical Cycle

**Intro.** The empirical cycle is the *idealised model* of how research moves from a raw observation to a tested, evaluated conclusion — and back again. It's "idealised" because real research rarely splits cleanly into these phases (no researcher says "today I'll do deduction"), but the model is a useful map of what *should* be happening. It has **five phases**.

**Key terms**
- **Empirical cycle** — the five-phase model (Observation → Induction → Deduction → Testing → Evaluation) describing the logic of scientific inquiry.
- **Induction** — reasoning *from specific instances to a general rule* (a "leap of faith").
- **Deduction** — reasoning *from a general rule to a specific, testable prediction*.
- **Hypothesis** — a concrete, testable, **falsifiable** prediction derived from a theory.
- **Falsifiable** — capable, in principle, of being proven wrong by evidence. This is what separates **science** from **pseudoscience**.
- **Population** — *all* the units you want to draw conclusions about (people, models, images, animals…).
- **Sample** — the subset of the population you actually collect data from.

### The five phases (with the running example)

The lecture used one running example: you notice you remember the **first and last** items of a shopping list (or digits of a phone number, or parts of a lecture) better than the middle.

| Phase | What happens | Shopping-list example | Classic example |
|---|---|---|---|
| **1. Observation** | Starting point: a question, obstacle, idea, problem, or unexpected event — from experience, imagination, or prior research | You notice first/last items are easier to recall | Newton's apple; Archimedes in the bath ("Eureka") |
| **2. Induction** | Build a *general rule/theory* from specific instances (a leap of faith) | "There's a **U-shaped** relation between an item's order and its recallability" | Newton generalising from one apple to *all* objects |
| **3. Deduction** | Infer a *specific, testable, falsifiable* prediction from the rule | "Given 10 random words, people will recall the first and last best" | — |
| **4. Testing** | Conduct a study: draw a sample, collect data, analyse it | Run a memory experiment, plot recall against position | — |
| **5. Evaluation** | Confirm or falsify the theory; reflect; plan follow-up | Does the U-shape appear in the data? What next? | — |

**On falsifiability (the boundary with pseudoscience).**
The lecturer role-played a "mentalist reading auras." When a guess was wrong, he had a built-in excuse ("too many skeptical vibrations in the air"), and he made claims so vague (*both* introverted *and* extroverted) that they fit almost anyone — leaning on the audience's **confirmation bias**. Because no possible result could ever prove him wrong, the claim is **unfalsifiable** → **pseudoscience**. A genuine hypothesis must be able to fail.

> **Note on phase 5:** "Falsification" is rarely clean. A failed prediction might mean the theory is wrong — *or* that the study was poorly implemented, participants weren't paying attention, etc. So we evaluate cautiously and reflect on what could have gone wrong.

> **Reality check:** Phases aren't sharply separated and can be filled in differently depending on the research. In *this course's assignment*, your "observation" phase is handed to you — you start from a given paper (Leong & Lake) and build on it, rather than inventing a topic from scratch.

---

## 3. Validity

**Intro.** Once you have data, the central question is: **can we trust what the study claims?** Validity is the umbrella concept for "are the claims correct, did we measure what we intended, and are there no alternative explanations?" Two forms dominate this lecture — **external** validity (does it generalise?) and **internal** validity (is the causal story right?). A recurring theme is that these two often *trade off* against each other.

**Key terms**
- **Validity** — the degree to which a study's claims are correct and free of alternative explanations.
- **External validity** — the extent to which findings **generalise** to other people, settings, items, or time periods (incl. lab → real world).
- **Internal validity** — the extent to which the study supports a **trustworthy causal claim**, free of confounds.
- **Sampling frame** — the list of all elements of a population from which a sample is drawn.
- **Simple random sampling** — every element of the sampling frame has an equal chance of being selected.
- **Convenience sampling** — selecting whoever is *easiest to access* (e.g. first-year psych students).
- **Non-response bias** — distortion arising because the people who *don't* respond differ systematically from those who do.
- **Confound (confounding variable)** — a third variable that influences both measured variables, creating a spurious association.
- **Common response model** — the structure where one variable (e.g. temperature) causally drives *both* observed variables, which have no direct causal link to each other.
- **Correlational study** — measuring variables to see how they relate (no manipulation).
- **Experimental study** — manipulating variables with random assignment to rule out alternatives.
- **Independent variable (IV)** — the factor the researcher *manipulates*.
- **Dependent variable (DV)** — the outcome the researcher *measures*.
- **Between-subjects design** — each subject experiences *one* condition.
- **Within-subjects design (repeated measures)** — each subject experiences *all* conditions.
- **Order effects** — distortions from the sequence of conditions (e.g. practice/training, fatigue).
- **Counterbalancing** — varying the order of conditions across subjects to neutralise order effects.
- **Random assignment** — allocating subjects to conditions by chance, so pre-existing differences balance out.

### 3a. External validity — does it generalise?

The question: if we observe a relationship in *this* sample, does it hold for *other* samples, settings, and over time?

**Example (AI):** Commercial **gender-classification** systems (Buolamwini & Gebru) classify faces well for **lighter-skinned men** but perform **poorly on darker-skinned women**. A result that holds on one (skewed) set of faces does **not** generalise to a balanced set → an external-validity failure.

**Why sampling drives generalisation.** You almost never measure the whole population, so you draw a **sample**. How you draw it determines whether results generalise.

| | Simple random sampling | Convenience sampling |
|---|---|---|
| **How** | Randomly draw from a full list (sampling frame) | Take whoever is easy to reach |
| **Generalisation** | Stronger — more likely to represent the population | Weaker — sample may be unrepresentative |
| **Feasibility** | Often hard/impossible (can't list "all people"/"all faces") | Easy and cheap |
| **Example** | Randomly select employees from a roster | First-year psychology students; readily-available face photos |

> **Even random sampling can be biased — the non-response trap.** Suppose you email a *random* sample of employees to measure whether an AI assistant reduced their workload. People with the *highest* workload may be **too busy to reply**. Your responders look low-workload, but only because the busy ones are missing. **Lesson:** always ask not just *who is in* your sample, but *who is systematically left out*.

### 3b. Internal validity — is the causal story right?

The question: does X actually *cause* Y, or is there a **confound** / alternative explanation?

**Example 1 — Ice cream & sharks.** Ice-cream sales correlate with shark attacks. Neither causes the other; **temperature** drives both (hot days → more ice cream *and* more swimmers). Temperature is a **confound**, and this structure is a **common response model**.

```
            Temperature
           /            \
         +/              \+
   Ice cream sales   Shark attacks
        (no direct causal link between these two)
```

**Example 2 — Chocolate & Nobel prizes (Messerli, 2012).** Countries with higher *per-person* chocolate consumption win more Nobel prizes. Tempting causal story: chocolate → better cognition → prizes. But:
- **Confound:** national **wealth** drives both chocolate consumption *and* investment in science.
- **Reverse causation** is even logically possible (winners celebrate with chocolate).
- Because it's **correlational**, we *cannot separate* these explanations. This is exactly why we need stronger designs.

### 3c. Correlational vs. experimental research

| | Correlational | Experimental |
|---|---|---|
| **What you do** | *Measure* variables and see how they relate | *Manipulate* an IV, *measure* a DV |
| **Assignment** | None | **Random assignment** to conditions |
| **Causal claims** | Weak — confounds can't be ruled out | Strong — alternatives can be ruled out |
| **Example** | Chocolate consumption vs. Nobel prizes | Give one group chocolate, one a placebo; compare puzzle scores |

**Turning the chocolate question into an experiment (audience suggestion):** measure baseline cognitive performance (a puzzle), then give chocolate to one group and **not** the other, re-test, and compare the change between groups. Key ingredients: a **manipulated IV** (chocolate vs. none), a **measured DV** (puzzle performance), and **random assignment**.

**Manipulating variables — another AI example:** *Does chain-of-thought prompting improve reasoning accuracy?*
- **IV (manipulated):** prompt type (regular vs. chain-of-thought).
- **DV (measured):** benchmark accuracy, consistency, latency.

### 3d. Between- vs. within-subjects designs

Running example: *Does an AI coding assistant help programmers code faster?*
- **Within-subjects:** each coder does one task *with* the assistant and one *without*.
- **Between-subjects:** one group of coders works *with*, a separate group *without*.

| | Within-subjects (repeated measures) | Between-subjects |
|---|---|---|
| **Each subject sees** | All conditions | One condition |
| **Advantage** | Fewer subjects; each subject is **their own control**, so no pre-existing group differences | **No contamination** between conditions; no order effects |
| **Disadvantage** | **Order effects** (training/practice, fatigue); needs two *similar-but-different* tasks | **Pre-existing differences** between groups (e.g. one group more skilled) |
| **Fix** | **Counterbalancing** (randomise order; half do A→B, half B→A) | **Random assignment** to conditions |

> **Key nuance:** Counterbalancing reintroduces a small **between-subjects component** (different people get different orders). And random assignment only balances groups *on average over many studies* — with one or two studies, bad luck can still leave groups unequal.

### 3e. Ruling out alternative explanations

The defining feature of good experimental work is **eliminating** rival explanations.

**Example — "Clever Hans."** A horse seemed to do arithmetic by tapping its hoof. In reality it couldn't do maths — it read **subtle cues** from the experimenter/audience to know when to stop tapping. The *alternative explanation* (cue-reading), not the obvious one (equine arithmetic), was correct.

**Example — the placebo issue.** In a chocolate experiment, simply *receiving something* (a reward, a friendly experimenter) could improve performance, independent of cacao. Fix: give the control group a **placebo** — something equally sweet but without cacao — so the *only* difference between conditions is the variable of interest. The principle: **hold everything constant except the one thing you're studying.**

### 3f. The internal–external validity trade-off

| | High internal validity | High external validity |
|---|---|---|
| **Setting** | Tightly controlled, often artificial lab | Realistic, real-world conditions |
| **Strength** | Confident causal claims | Results generalise |
| **Weakness** | May not transfer to the real world | Hard to isolate causes (many confounds) |

> **The core tension:** the more you control a situation to nail down causation (internal validity), the more *artificial* it can become, weakening generalisation (external validity) — and vice versa. Managing this trade-off is one of the central challenges of research design.

---

## 4. Generative AI in Research

**Intro.** A contemporary issue: generative AI is increasingly used to *write* and even *produce* research. This raises questions about honesty, responsibility, and disclosure — and directly shapes what you're allowed to do in this course.

**Key terms**
- **Generative AI (genAI)** — AI systems (e.g. large language models) that generate text, code, or analyses.
- **Peer review** — independent experts evaluating a paper before publication and recommending acceptance/rejection.
- **Retraction** — formal withdrawal of a published paper (e.g. after misconduct or serious error).
- **Disclosure statement** — an explicit declaration of whether/how genAI was used in a piece of work.
- **Authorship (responsibility criterion)** — to be an author you must be able to take *responsibility* for the work; an AI cannot, so it cannot be an author.

### What's happening in the wild
- **Leftover LLM phrases in published papers.** Real (now-retracted) papers contained text like *"I'm very sorry, but I don't have access to real-time information… as I am an AI language model"* and *"Certainly, here is a possible introduction for your topic…"* — slipping past peer review.
- **An AI-generated paper got accepted (ICLR).** In an agreed-upon experiment with conference organisers, **three fully AI-generated papers** (including the experiments, with *real* code and analysis — **not** hallucinated, **not** fraud) were submitted; **one was accepted** by three reviewers. Raises the question: can genAI be a genuine *producer* of knowledge?
- **The "delve" study.** Analysing biomedical abstracts, researchers found word-frequency shifts (e.g. a spike in "**delve**") suggesting **≈13.5%** of 2024 abstracts were processed with LLMs. The effect on word use was **larger than the COVID pandemic's**. (Note: external-validity caveat — these opinions and patterns may shift over time as models improve.)
- **Authorship attempts.** ChatGPT was once listed as a co-author ("O'Connor & ChatGPT"); this was **corrected/retracted** because an author must take responsibility, which a model cannot.

### Policy summary

| Question | General research norm | **This course's rule** |
|---|---|---|
| Can AI be an author? | No — it can't take responsibility | N/A |
| Using AI for writing whole sections (results/methods)? | Widely seen as **inappropriate**, even if disclosed | **Not allowed** |
| Using AI for spelling/grammar/style? | Often acceptable *if disclosed* | **Allowed** |
| Disclosure required? | Often a genAI-use statement is required | **Yes** — describe prompts, original output, and a reflection on use |

> **Required course statement (add one):**
> - *"We did not use (generative) AI in the preparation and execution of this assignment beyond what is disclosed in the current section."*
> - *"No (generative) AI was used in the preparation and execution of this assignment."*

---

## Exam-style checkpoint (from the lecture)

1. *"If this hypothesis is true, students using the app should score higher on the test."* Which phase? → **C. Deduction** (general rule → specific testable prediction).
2. *Internal validity is mainly concerned with…* → **B. Whether the study shows a trustworthy causal relationship.**

---

## Final Recap — How It All Connects

Think of the lecture as one continuous argument about **trustworthy knowledge**, built in four layers:

1. **Scientific thinking is the foundation.** Human intuition is systematically biased — **confirmation bias**, the **availability** and **representativeness** heuristics, **hindsight bias**. *Because* we are "the easiest person to fool," we can't rely on intuition; we need a disciplined process.

2. **The empirical cycle is that disciplined process.** It channels raw **observations** into a general theory (**induction**), then into a **falsifiable** prediction (**deduction**), which is **tested** on a *sample* and finally **evaluated**. The falsifiability requirement is the direct cure for confirmation bias — it forces us to look for the evidence that could prove us *wrong* (the "3" card), and it's exactly what separates science from pseudoscience (the aura-reading mentalist).

3. **Validity is the quality control on that process.** Testing requires a sample, so **external validity** asks whether the sample's results *generalise* (the gender-classifier failure; the non-response trap). Evaluation requires a causal claim, so **internal validity** asks whether that claim survives **confounds** (chocolate↔wealth, ice cream↔temperature). The tool for securing internal validity is the **experiment** — manipulate an **IV**, measure a **DV**, use **random assignment**, choose **within-** or **between-subjects** wisely, and **rule out alternatives** (Clever Hans, placebos). But control comes at a price: the **internal–external validity trade-off** means the cleanest causal studies are often the least realistic.

4. **GenAI in research is where all of this is being tested right now.** Knowing the biases, the cycle, and validity is precisely what lets you critically judge AI-produced research — an AI-written paper can pass peer review, "delve" can flood the literature — and it's why this course demands **transparent disclosure** rather than blind use.

**One-line throughline:** *Don't fool yourself (thinking) → follow a falsifiable process (empirical cycle) → check that the results generalise and the causes are real (validity) → apply that same scrutiny to AI in research (genAI).*
