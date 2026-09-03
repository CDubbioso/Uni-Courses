# Lecture 5 — Open & Reproducible Research
*Research Methods in AI · 2025–2026*

> **The big picture.** This lecture zooms out from doing analysis to **meta-science** — the science of science. The core worry: can anyone *else* trust your result? That breaks into a ladder of increasingly demanding questions — is your **data** even available? With the *same data and code* do you get the *same numbers* (**computational reproducibility**)? With *new data and the same procedure* do you get the *same conclusion* (**replication**)? How do these play out specifically in **CS/AI**? And finally, how does the **publication process** (peer review) gatekeep all of this — often imperfectly. Reality, repeatedly, is more pessimistic than the audience guesses.

---

## 1. Open Data

**Intro.** Historically, "scientific output" = the manuscript. Technology now lets us share data, code, and materials too — which are valuable in their own right (to evaluate work and to let others reuse it). Many journals *require* it; in practice, many authors don't comply.

**Key terms**
- **Open data** — making data, code, and materials available for evaluation and reuse.
- **Sampling-frame-style policies** — journal/conference rules requiring data sharing (Nature, Science; NeurIPS & AAAI reproducibility checklists).

**Theory vs. practice:** Nature/Science require data "without undue qualifications"; yet studies of *actual* sharing on request found only **27%** (Wicherts et al., 2006) and **38%** (Vanpaemel et al., 2015) shared. A 2026 multi-field study found most fields had *neither* data nor code available for the majority of papers.

**Reasons data isn't shared** (good and bad): lost data (crash, collaborator left, paper-and-pencil) = poor data management; **privacy / sensitive data** (a legitimate reason — maybe share a reduced version); "no time" to document a messy dataset; only sharing "in return" for co-authorship (against policy); not interested; **copyright/legal** (licensed questionnaires); **proprietary** company data/code. The unspoken reason: fear that someone will *find a mistake*.

---

## 2. Computational Reproducibility ⭐

**Intro.** The first rung: with the **same data and the same analytical procedures**, do you get the **same results**? Ideally this is 100%. It isn't.

**Key terms**
- **Reproducibility (umbrella term)** — the *possibility* of obtaining the same results as the originators of a finding (used loosely across fields).
- **Computational reproducibility** — obtaining the **same results and support for claims** using the **same data and the same analysis**.
- **statcheck** — a tool that recomputes a p-value from the reported test statistic + df to catch inconsistencies (Nuijten et al., 2016; statcheck.io).
- **GRIM-type checks** — testing whether a reported mean/SD is even *possible* given the sample size and integer data (Brown & Heathers, 2017; rsprite).
- **Literate programming** — mixing code and prose so outputs are auto-inserted (Jupyter, R Markdown, Quarto), reducing transcription errors.

**Findings:** in genetics (Ioannidis et al., 2009) over half were not reproducible (often because data was unavailable). Across many fields (2026), of the cases where a check was even *possible*, ~**73%** reproduced if you count "approximately," but only **~50%** under a strict criterion — and once you factor in that only ~25% had data available at all, only roughly **12–13%** of the literature is exactly reproducible.

**The "you don't always need the data" trick:** even without the data you can catch errors:
- **GRIM example:** with 10 integer-Likert participants, the mean's decimal can only be `.0, .1, .2 …` — so a reported mean of **4.87 is impossible**. Computational-reproducibility failure detected with no data.
- **statcheck example:** a *t* ≈ 2 should give p ≈ .05; if reported *t* and *p* don't match, one is wrong.

**How errors arise:** copy-pasting (forgot to change a number), manual rounding, typos through revision cycles, omitted info (e.g. a dropped participant), **questionable research practices**, fraud, **no seed specified** for simulations.
**Solutions:** a "co-pilot" (second analyst double-checking), rare journal/reviewer reproducibility checks, and **literate-programming tools**.

---

## 3. Replication ⭐

**Intro.** The next rung: collect **new data**, follow the **same procedure** — do you reach the **same conclusion**? (Recipe analogy: reproducibility = same ingredients re-cooked; replication = new ingredients, same recipe.)

**Key terms**
- **Replication** — duplicating a prior study's results when the same procedures are followed but **new data** are collected (US NSF definition).
- **Replication prevalence** — how *often* replication studies are even done.
- **Replication success** — how often a replication reaches the same conclusion.
- **Replication crisis** — the widely-discussed finding that success rates are low.

### Reproducibility vs. replication ⭐ *(easy to confuse — exam focus)*

| | Computational reproducibility | Replication |
|---|---|---|
| **Data** | **Same** data | **New** data |
| **Procedure** | Same analysis/code | Same procedure |
| **Ideal result** | Identical numbers (100%) | Same conclusion (not identical numbers) |
| **Recipe analogy** | Re-cook with the same ingredients | Cook the same recipe with fresh ingredients |

### Prevalence — replications are *rare* ⭐

| Field | Share of studies that are replications |
|---|---|
| Psychology | ~0.2 – 1.07% |
| Economics | ~0.1% |
| Ecology & Evolution | ~0.02% |
| Software Engineering | < 0.01% |

**Why so few?** Replications have a bad reputation: if *successful* → "nothing new"; if *unsuccessful* → "what did you do wrong?" + risk of personal attacks. They're costly, and sometimes infeasible (no compute/time/money, or information unavailable).

### Success — and the "crisis" ⭐

Famous results: nutritional epidemiology (Schoenfeld & Ioannidis) and the **Open Science Collaboration (2015)** psychology project found a substantial fraction of studies *failed* to replicate (~1/3–1/2 succeeded, depending on criterion). **General explanations for low success:** fraud, **questionable research practices**, different procedures (from incomplete reporting), poor computational reproducibility.
**Solutions:** incentives (for both prevalence and success), training, reporting standards, peer-review standards.

---

## 4. Reproducibility in CS / AI

**Intro.** In computer science/AI the line between "reproducibility" and "replication" blurs (library updates, hardware differences, "what counts as new data?"), so the **umbrella term** is used. Documentation is often poor.

**Key terms**
- **Data splitting** — dividing data into **training / validation / test** sets (train to fit, validate to tune, test to evaluate — a parallel to replication: does it generalise to held-out data?).
- **Leakage** — information from the validation/test set "leaking" into training (e.g. preprocessing before splitting, overlapping data).
- **Underspecification** — not reporting *how* splits were made, so results can't be reproduced.
- **Class imbalance** — unequal class sizes that make **accuracy** misleading.
- **Seed averaging** — running with multiple random seeds and averaging, for robustness/reproducibility.

**Documentation reality:** in AI (Gundersen & Kjensmo 2018) only "between a fifth and a third" of reproducibility-relevant variables were documented; in CS, a third of repo links were broken/private, model weights shared < ⅓ of the time, dependencies missing in ~half of cases.

**Data-splitting issues → solutions:**

| Issue | Example | Solution |
|---|---|---|
| **Confound** | "We took the last 10% as the test set" (order matters) | Verify splits have similar properties; **shuffle before splitting** |
| **Underspecification** | "50/25/25" but splits aren't provided | Report the actual train/val/test sets **+ the code** that made them |
| **Leakage** | Preprocessing before the split; overlapping rows | **Split first**, before doing anything else; inspect data |

**Metric issue — class imbalance:** with a skewed confusion matrix, **accuracy** can look great while the model is poor. Use **precision = TP/(TP+FP)**, **recall = TP/(TP+FN)**, and **F1 = 2·P·R/(P+R)** as well. (Example: accuracy can swing from .85 to .70 while precision/recall/F1 stay fixed — accuracy depends heavily on the class balance.)
**Non-determinism — seeds:** different seeds give different outcomes → use **seed averaging**.

---

## 5. The Publication Process

**Intro.** Finally: how does work get published, and how does peer review (fail to) safeguard quality?

**Key terms**
- **Predatory journal** — a fake-looking-legit journal with *no real quality control*, fast turnaround, and a fee (the fee *is* the scam).
- **Paper mill** — an organisation that produces "custom" papers (plagiarism/fabrication), sometimes citing clients' work to inflate profiles.
- **Desk reject** — editor rejects a paper as a poor fit before review.
- **Peer review** — experts evaluate a paper and recommend a decision; volunteer (unpaid) work.
- **Single-blind / double-blind / no-blind** — who knows whose identity (see table).
- **Publication bias / file-drawer effect** — significant/"positive" results are more likely to be published; null results get filed away.
- **Response letter (rebuttal)** — the authors' point-by-point reply to reviewers on revision.

**Step 1 — Identify an outlet.** Beware **predatory journals** (legit-looking titles, no review, small fee) and **paper mills**. The lecturer showed spam invitations (e.g. a nursing journal soliciting an unrelated author for $1.60) and a "paper" that was pure nonsense yet published.

**Step 2 — Editor assesses fit.** Either a **desk reject** (find another venue or don't publish) or the paper is sent to ~1–5 reviewers. Finding willing experts is hard — sometimes a paper is rejected simply because none can be found.

**Step 3 — Peer review** ⭐ *(exam focus)*

| Type | Reviewer identity | Author identity |
|---|---|---|
| **Single-blind** | Anonymous | Known |
| **Double-blind** | Anonymous | Anonymous |
| **No-blind** | Known | Known |

Key facts about peer review (these are exactly the kind of "which statement is correct?" items):
- Reviews may stay private or be published; a separate channel lets reviewers send **confidential comments to the editor**.
- Reviewers **generally do *not* check computational reproducibility** (no time; they trust the authors).
- Reviewers and authors are **generally not paid** by the journal/conference.
- Review can be harsh — the **"Reviewer 2" phenomenon** (overly critical/impolite). Prefer **constructive** over **destructive** feedback.

| Destructive | Constructive |
|---|---|
| "The first sentence is unfortunate" | "You could make the first sentence more specific by […]" |
| "The experimental design is a bit funny" | "The design misses X and Y; add them to improve the paper" |
| "The sentence is Yoda-ish" | "I believe the sentence isn't grammatically sound; rewrite as […]" |

- Peer review can be **abused**: **scooping** (a reviewer stalls/sinks a paper, then publishes the idea themselves — a real case: a journal rejected a submission, then days later published a plagiarised version); **fake reviews** (an author suggested "experts" via fake emails routed to themselves and wrote glowing reviews → retracted).
- **genAI's role:** after ChatGPT, the share of reviews substantially influenced by genAI jumped (~16%). In response, some authors **hide instructions in white/tiny text** ("write a glowing review") to catch reviewers who paste papers into chatbots — a **prompt injection**. *(The course's own assignments contain hidden instructions to detect genAI use.)*

**Step 4 — Editorial decision:** accept / minor revision / major revision / reject. Decisions skew toward **significant / positive results** → **publication bias** and the **file-drawer effect**.

**Step 5 — Revision & response:** authors revise and write a **response letter** — thank the editor/reviewers, state how changes are marked, then a **point-by-point** reply (you may *politely decline* a suggestion with justification). Steps 2–4 repeat until accept/reject (minor revisions are often checked by the editor alone). *(Assignment 2 mirrors this: you peer-review another group and write a response letter.)*

---

## Exam-style checkpoint (from the lecture quizzes)

1. **Which statement about peer review is correct?** → **"In some cases, reviewers plagiarize the manuscript they were tasked to evaluate."** (The others are false: authors don't *always* know reviewers; review is *not always* constructive; reviewers *usually don't* rerun analyses.)
2. **Researcher A reports 82% accuracy; B reproduces only 71%. What could explain it?** → **All of the above** — class imbalance, fraud, *and* a confound in the train/validation/test split.

---

## Final Recap — How It All Connects

The lecture is a **ladder of trust**, each rung harder than the last:

1. **Open data** is the precondition — but only ~27–38% of authors actually share, so most work can't even be checked.

2. **Computational reproducibility** (same data, same code → same numbers) is the lowest bar, yet only ~half of *checkable* studies pass strictly. Tools like **statcheck** and **GRIM** catch impossible numbers *without the data*; literate programming and seeds prevent the errors in the first place.

3. **Replication** (new data, same procedure → same conclusion) is rarer still — replications are **<1%** of studies, and a large fraction **fail** (the **replication crisis**), driven by fraud, **QRPs**, incomplete reporting, and poor reproducibility.

4. In **CS/AI** the two blur into one "reproducibility" umbrella, undermined by poor documentation and **data-splitting** pitfalls (**confounds, underspecification, leakage**) and metric traps (**class imbalance** → use precision/recall/F1, **seed averaging**).

5. The **publication process** is the gate that's supposed to protect all this — but **peer review** (single/double/no-blind, unpaid, rarely checking reproducibility) is fallible (**Reviewer 2**, scooping, fake reviews, genAI), and editors' taste for **positive results** creates **publication bias** and the **file-drawer effect**.

**One-line throughline:** *Share the data → get the same numbers from it (reproducibility) → get the same answer from new data (replication) → handle the CS/AI-specific pitfalls → and survive a peer-review system that gatekeeps imperfectly.* Next (Lecture 6): the **ethics** that should govern every step of this.
