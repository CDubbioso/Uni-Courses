# Lecture 6 — Ethics in Research and AI
*Research Methods in AI · 2025–2026 · Gabriel Barroso*

> **The big picture.** Ethics isn't a final add-on — it *permeates every step* of research, from design to reporting, and it reinforces the rigor from earlier weeks. The lecture builds one flexible ethical **framework** (Belmont: three principles, each with an application), stress-tests it on an **infamous case** (Facebook's 2014 emotion experiment), threads ethics through the **research process** (collection → storage → reporting, where **HARKing** and other questionable practices live), and ends with **AI ethics** and the EU AI Act.
>
> *Note: these notes are built from the lecture recording (no slide file was provided).*

---

## 1. Why Ethics Matters

**Intro.** Research regulation, like much human regulation, grew out of disasters. Ethics protects participants — but it's also about **rigor**: unethical work is often *bad* work, and bad research can cause real-world harm (e.g. the retracted paper falsely linking vaccines to autism).

**Key terms**
- **Belmont Report** — the foundational US framework (post-Tuskegee) giving three flexible ethical principles, designed to adapt to new problems (including AI).
- **Institutional Review Board (IRB)** — a body (at a university/government institution) that reviews research proposals for ethics *and* technical soundness before data collection. (Leiden's Faculty of Science has one.)

**The cautionary case — Tuskegee syphilis study (1932–1972):** ~400 African-American men with syphilis were studied *untreated* — they weren't told, could infect families, and **penicillin was withheld** even after it became the cure, so researchers could study the disease via autopsy. Promised to last 6 months, it ran **40 years**, stopping only after a researcher leaked it. Other frameworks exist (Helsinki Declaration, APA guidelines, Hippocratic oath), but Belmont is used here for being broad and adaptable.

---

## 2. The Belmont Framework ⭐ *(exam focus — esp. beneficence vs. justice)*

**Intro.** Three principles, each paired with a concrete **application** that operationalises it.

**Key terms**
- **Respect for persons** — treat people as **autonomous agents** who can make informed decisions; give *extra* protection to those with limited capacity (mental illness, minors, age) and **vulnerable populations** (prisoners, minorities). → Applied via **informed consent**.
- **Beneficence** — extends "do no harm": actively keep participant well-being in mind, **minimise risks**, consider immediate *and* long-term effects. → Applied via **risk–benefit assessment**.
- **Justice** — **fair distribution of benefits and burdens**; counter manipulation, coercion, and bias in *who* bears the costs vs. *who* reaps the gains. → Applied via **fair subject selection**.

### The three principles at a glance ⭐

| Principle | Core idea | Application | Failure example |
|---|---|---|---|
| **Respect for persons** | Autonomy; protect the vulnerable | **Informed consent** | Enrolling people who can't consent (minors) without guardians |
| **Beneficence** | Maximise well-being, minimise harm | **Risk–benefit assessment** | Exposing people to harm without weighing/monitoring it |
| **Justice** | Fair spread of benefits & burdens | **Fair subject selection** | Burdens fall on a vulnerable group; benefits go to another |

> **Beneficence vs. justice ⭐** — a frequent point of confusion. **Beneficence** is about the *magnitude* of harm vs. good (is this study worth its risks, short- and long-term?). **Justice** is about the *distribution* — are the *same* people bearing the burdens who get the benefits? The Tuskegee/drug-testing pattern (test on a vulnerable group, benefit a different group) is a **justice** violation; subjecting people to undue harm at all is a **beneficence** violation. (Real blind spot: much heart-attack research used only male participants, so women's different symptoms were missed — a justice failure.)

### The applications, unpacked

**Informed consent ⭐ — three required elements:**

| Element | Meaning |
|---|---|
| **Information** | Convey what will happen, in language the participant can meet (minimal jargon; translators if needed) |
| **Comprehension** | The participant must actually *understand* — information without understanding is useless |
| **Voluntariness** | Participation (and withdrawal) must be a *real, free choice* — opt-in, no coercion |

**Risk–benefit assessment:** done *before* data collection, with co-authors and the IRB; covers **physical, psychological, social, and legal** risk (even reputational damage), each weighted by **likelihood** (like a medical "X% experience nausea" disclosure).

**Fair subject selection ⭐:** an impartial, justified recruitment procedure free of bias/prejudice (clinical-trial demographics often don't match the population; for years, pain research wrongly assumed Black patients had higher pain tolerance → under-treatment).

> **Three retrospective questions** the lecturer recommends for any (especially older, controversial) study: *Was consent valid? Were the risks justified? Was subject selection fair?*

---

## 3. Case Study — Facebook's 2014 Emotional-Contagion Experiment

**Intro.** ~700,000 users had their feeds manipulated (more positive *or* more negative posts) to test whether emotions could be influenced. Applying Belmont:

| Principle | What went wrong |
|---|---|
| **Respect for persons / consent** | **No information** (users didn't know they were in a study), so **no comprehension**, and **no voluntariness** (not opt-in). Terms of service didn't even cover experiments at the time. |
| **Beneficence** | Short-term harm per user seems small, but at Facebook's **scale** the accumulated negative experience is large; **long-term** effects unknown; **no harm monitoring**. |
| **Justice / selection** | Inclusion criterion was merely "be a user," so it swept in **minors** (can't consent) and likely **depressive** users, for whom negative content means something very different. |

**Aftermath / fixes that *should* have applied:** opt-in recruitment, prior IRB/company review, exclusion of minors (or guardian involvement), and a **prospective harm assessment**. The university partner's "we just used the data Facebook collected" defence highlights **researcher responsibility**. (A result worth noting: users fed more negative content also *posted less* — relevant to online expression.) **Lesson:** ethical limits aren't bureaucratic annoyances — they're the *strength* of the academic context, precisely what's missing when research happens only inside private companies (as with much LLM work).

---

## 4. Ethics Across the Research Process

**Intro.** The lecturer maps ethical considerations onto the same pipeline from earlier weeks: **collection → storage → analysis/reporting**.

**Key terms**
- **robots.txt** — a file on a website specifying what may/may not be scraped; respect it, plus **rate limits** and **terms of service**.
- **GDPR** — EU regulation treating **data protection as a human right**; lawful processing needs consent, legal obligation, or legitimate interest.
- **Data minimisation** — collect only what's necessary, for a stated purpose, with a **retention period**, and an honoured **right to deletion**.
- **Pseudo-anonymisation** — replacing identifiers with a code/noise; **still personal data → still under GDPR** (re-identification is often possible).
- **(Full) anonymisation** — no individual can be recovered (e.g. via aggregation); then it's *not* personal data and falls outside GDPR.
- **Research degrees of freedom** — the many analysis/reporting choices a researcher can make.
- **Garden of forking paths** (Gelman & Loken) — the metaphor for all those possible analytic paths.
- **HARKing** — *Hypothesising After the Results are Known* (a.k.a. the **Texas Sharpshooter**: shoot first, draw the target around the holes).
- **p-hacking** — tweaking choices until a significant p-value appears.
- **Selective reporting** — reporting only the (significant) results you like.

### Responsible data collection (scraping)
For any large site (Reddit, X, Instagram): obey **robots.txt** (which fields are allowed — often *not* usernames, location, or timestamps), respect **rate limits** (avoid DDoS-like overload), and **read the terms of service** (some forbid certain uses or commercial use).

### Data storage — GDPR

| GDPR principle | Meaning |
|---|---|
| **Lawful basis** | Consent, legal obligation, or legitimate interest |
| **Data minimisation** | Collect only what's necessary for a stated purpose |
| **Retention + deletion** | Hold data only for a set period; honour deletion requests |
| **Access control** | Track/limit who can see the data and why |

**Pseudo- vs. full anonymisation:**

| | Pseudo-anonymisation | Full anonymisation |
|---|---|---|
| **Method** | Replace identifiers with a code / add noise | Cannot recover any individual (e.g. aggregate stats only) |
| **Re-identification** | Often possible (combine with other info) | Not possible |
| **GDPR status** | **Still personal data → under GDPR** | **Not** personal data → outside GDPR |

> Subtle re-identification risk: even without names, "one girl of age X in this class" can be identifiable — hence **data minimisation** in what you publish.

**Belmont ↔ GDPR parallel:** informed consent ↔ lawful basis; risk minimisation ↔ **data** minimisation; justice/fairness ↔ the enforceable legal-rights framework (fines).

### Analysis & reporting — questionable research practices ⭐ *(exam focus)*

Because of **research degrees of freedom** (the **garden of forking paths**), the *same* dataset can yield very different p-values depending on choices (one paper found **200+** defensible analytic decisions, with p-values swinging widely).

| Practice | What it is | Why it's a problem |
|---|---|---|
| **Selective reporting** | Report only significant results | Hides the full picture; inflates apparent effects |
| **p-hacking** | Massage choices until p < .05 | Manufactures false positives |
| **HARKing** ⭐ | Invent the hypothesis *after* seeing results, present it as a priori (**Texas Sharpshooter**) | Turns post-hoc noise into a "prediction"; non-replicable |

> These connect straight back to Lecture 5's low replication rates: **QRPs**, selective reporting, and HARKing are major *causes* of findings that don't replicate.

---

## 5. AI Ethics

**Intro.** A young, fast-moving field (post-ChatGPT). The lecture applies the *same* Belmont lens to recurring AI concerns.

**Recurring concerns → Belmont response:**

| Concern | Belmont framing | "Fix" direction |
|---|---|---|
| **Annotator exploitation** (underpaid labelers in poorer countries) | **Justice** — burden on a vulnerable group, benefit elsewhere | Fair selection & pay; careful alignment-labelling (exposes annotators to harmful content) |
| **Bias** (models replicate/amplify historical bias in hiring, admissions) | **Justice** | Bias **audits**; self-regulation |
| **Black-box opacity** (can't inspect decisions; protected categories) | **Respect / autonomy** | Transparent/explainable models; **right to contest** decisions |
| **Harm at deployment** (paranoia, addiction; harmful outputs) | **Beneficence** | **Harm testing before deployment** |
| **Environmental cost** (data centres) | **Risk–benefit** | Weigh benefits vs. damage |
| **Unequal access** (richer users get better models) | **Justice** | Equitable access; don't widen inequality |

**EU AI Act — the first major legal framework**, classifying AI by **risk** (more risk → more regulation):

| Tier | Examples | Rule |
|---|---|---|
| **Unacceptable** | Social scoring, manipulative AI, emotion inference in work/public spaces | **Banned** |
| **High risk** | Hiring tools, credit scoring, education admissions | Strictest regulation |
| **Limited / minimal** | Chatbots, AI-enabled games/film | Mainly **disclosure** (people must know they're interacting with AI) |

---

## 6. Presentation & Visualisation (brief)

**Intro.** Communication is part of research. Reuses Lecture 4/5 points; reproducible, honest figures matter.

**Common sins to avoid:** **truncated y-axis** (exaggerates differences — the classic Fox News bar chart from 35→39 starting above zero), **not showing uncertainty** (state whether error bars are SE, SD, or CI), gratuitous 3-D, cluttered plots with no clear message, and **inconsistent axes** when combining plots. **Accessibility:** ~8% of men are colour-blind, so avoid red–green-only encodings; use colour-blind-safe palettes (ColorBrewer) and check (e.g. colorblindness simulators). Colour should *carry information*, not just decorate.

---

## Scenario poll takeaways (ethical reasoning in practice)

- **Sharing scraped Reddit data for reproducibility:** most chose *not* to release raw usernames — indexing public posts in a paper invites attention and **reputational risk** (beneficence/justice); pseudo-anonymisation may be insufficient (re-identification).
- **Model trained on copyrighted images wins a benchmark; court later finds no infringement:** majority said still **unethical** — *legal ≠ ethical* (you arguably owed creators permission/compensation).
- **Undisclosed AI mental-health chatbot (40% more engagement if not disclosed):** a clear split between "**consent is non-negotiable**" and pragmatic non-disclosure — note the **misalignment** (the bot is incentivised to keep users engaged, not to resolve their problems) and the felt **betrayal** when users discover it.
- **Reusing a colleague's already-consented dataset under publish-pressure:** most would "**ask the ethics board**," highlighting the gap between **theoretical** ethics (ask for approval) and **practical** incentives (asking risks rejection) — *beware the incentive structure*.

---

## Final Recap — How It All Connects

Ethics is the connective tissue of the whole course, not a postscript:

1. **A framework first.** Born from disasters (Tuskegee), the **Belmont** principles — **respect for persons, beneficence, justice** — each get an application: **informed consent** (information + comprehension + voluntariness), **risk–benefit assessment**, and **fair subject selection**. The key distinction: **beneficence** weighs *how much* harm vs. good; **justice** asks whether the *same people* bear the burdens and gain the benefits.

2. **Tested on a real case.** The **Facebook 2014** study fails all three — no consent, scale-amplified harm with no monitoring, and a selection that swept in minors and depressive users — showing why ethical limits are a *strength*, not red tape.

3. **Threaded through the pipeline.** In **collection**, consent + responsible scraping (**robots.txt**, rate limits, ToS); in **storage**, **GDPR** (lawful basis, **data minimisation**, deletion; **pseudo-** vs. full **anonymisation**); in **reporting**, the **garden of forking paths** breeds **questionable research practices** — **selective reporting, p-hacking, and HARKing** — which are precisely the causes of the failed replications from Lecture 5.

4. **Applied to AI.** The same Belmont lens names AI's harms (annotator **justice**, **bias**, **black-box** opacity, deployment **beneficence**, access **justice**), now backed by the **EU AI Act's** risk tiers. And honest **visualisation** (no truncated axes, show uncertainty, colour-blind-safe) is the ethical last mile of communication.

**One-line throughline:** *Respect people (consent), do more good than harm (beneficence), spread benefits and burdens fairly (justice) — and carry that judgment through collection, storage, analysis, reporting, AI, and even your final figures.*

---

## Course-wide connections (all six lectures)

- **L1 (Scientific thinking → validity)** gives the reasoning standards; **L6** shows that violating them (HARKing, selective reporting) is both an *epistemic* and an *ethical* failure.
- **L2 (Data collection)** raises consent/observation issues that **L6** formalises under respect-for-persons and GDPR.
- **L3 (Simulation)** and **L4 (Analysis)** create the **research degrees of freedom** that **L6** warns can be abused, and that **L5** shows undermine reproducibility/replication.
- **L5 (Reproducibility)** and **L6 (Ethics)** are two sides of *trustworthy science*: L5 asks "can others verify it?", L6 asks "should we have done it, and did we do it honestly?"
