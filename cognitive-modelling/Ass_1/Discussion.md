# 4 Discussion

In this report we examined whether in-group favouritism produced by attitude priming differs in magnitude from out-group derogation. We analysed accuracy and response times of 12 Caucasian participants and compared DDMs in which the face shifts the starting point or changes the drift rate. Incompatible trials led to more errors, slower correct responses and faster errors. The starting-point model fitted best, and both faces shifted the starting point in the expected direction (in-group: z = 0.57; out-group: z = 0.41), but the shifts did not differ significantly in size.

The compatibility effect replicates Fazio et al. (1995) and supports the view that attitudes are activated automatically (Fazio et al., 1986; Greenwald & Banaji, 1995). The starting-point model had the lowest total BIC and beat both drift models for every participant. When the face instead added a fading drift, its time constant was only 11–41 ms, close to the lower limit of 10 ms, making it practically a shifted starting point. This suggests that the face biases the decision before evidence from the word accumulates, rather than changing how the word is evaluated, in line with Todd et al. (2021). A shifted start also explains the fast errors on incompatible trials. Unlike Todd et al. (2021), we compared each starting point to the midpoint, which suggests that both faces contribute to the bias.

Contrary to our expectation based on Brewer (1999), the in-group shift was not larger; if anything, the out-group shift was larger (0.09 against 0.07). With 12 participants, however, this does not show that both shifts are equal. The effect also varied between people, as Fazio et al. (1995) reported: for four participants, the model without a face effect was slightly preferred. Finally, speed differences between participants mainly reflected non-decision time and accuracy differences reflected drift rate, with nearly constant boundary separation, so slower participants were not more accurate (Figure 1).

The main limitation is the lack of a neutral prime: the midpoint is only assumed to be neutral. Our asymmetry test is mathematically identical to testing whether the average starting point differs from the midpoint, so a general tendency to answer "negative" would look exactly like a larger out-group shift. Unlike Fazio et al. (1995), who measured a baseline without primes, we cannot separate the two. Furthermore, the sample is small and only Caucasian. Our basic DDM, without across-trial variability and with a fixed lapse rate, slightly under-predicted compatible errors around 0.5 seconds, and we ran no parameter recovery. A face effect on non-decision time and a combined starting-point and drift model were also not tested.

Future work could add a neutral prime, such as a scrambled face, to measure the unbiased starting point. Recruiting black participants would test whether the bias is reciprocal, as Fazio et al. (1995) found, and a hierarchical Bayesian DDM (Wiecki et al., 2013) would make better use of the limited trials per participant. Varying the interval between face and word would show how quickly the bias builds up.

---

## Notes (not part of the section)

**Word count:** 496 words (plain count, citations included), so it fits the 500-word limit.

**What changed compared to the previous version**

- Both DDM placeholders are replaced with the actual results: starting-point shifts, no significant asymmetry, the model comparison, and the fading-drift result.
- The limitations that no longer applied are gone: "untrimmed RTs", "few errors per combination", and "only the starting point was tested".
- The neutral-baseline limitation now names the "negative" direction and states that the asymmetry test equals a test of a general response bias.
- The White & Poldrack (2014) argument is replaced by the model comparison and the model's fit of the fast errors. **Delete White & Poldrack (2014) from the reference list.** Wiecki et al. (2013) is still cited.
- Individual differences are now explained with the fitted parameters instead of Figure 1 alone.

**Where each number comes from (notebook)**

- z = 0.57 / 0.41 and the asymmetry test: cell 17 (t(11) = −1.31, p = .22)
- Shift sizes 0.07 / 0.09: cell 19, mean distance of each starting point from 0.5
- Model comparison (lowest total BIC; beats both drift models for all 12; no-face model slightly preferred for 4, ΔBIC < 6): cells 21–22
- τ = 11–41 ms, lower bound 10 ms: cell 21
- Model under-predicts compatible errors around 0.5 s: cell 23 figure
- Fixed lapse rate: PyDDM's `gddm` default `mixture_coef = 0.02`, i.e. 2%

**Computed from the notebook's printed per-subject tables (cells 4 and 15). Not in the notebook yet; add these to Results:**

- Mean RT vs. accuracy across participants: r = −0.17, p = .59. The Results text and the Figure 1 caption claim a negative correlation, which this does not support.
- Mean RT vs. non-decision time: r = .99. Accuracy vs. mean drift rate: r = .98. Boundary separation B: 0.48–0.52 for everyone.
- If the §0 check on B fails, replace the last sentence of paragraph 3 with: _"Finally, slower participants were not more accurate (Figure 1), suggesting that speed and accuracy reflected different processes."_

**Must be consistent elsewhere in the report**

- **Introduction:** "without a neutral baseline, one cannot tell… (Fazio et al., 1995)" now contradicts the Discussion ("Unlike Fazio et al. (1995), who measured a baseline without primes"). Suggested fix: _"…without a neutral baseline, which Fazio et al. (1995) obtained from a separate block without primes, one cannot tell whether a face adds positivity or negativity."_
- **DDM Methods/Results (peer)** must define everything the Discussion uses:
  - z on a 0–1 scale (0 = "negative" threshold, 1 = "positive" threshold, 0.5 = midpoint)
  - BIC
  - the four models
  - the fading drift and its time constant τ
  - the RT trimming (0.25–1.5 s; 16 of 5520 trials removed)
  - the fixed 2% lapse rate
- If Results labels the hypotheses H1/H2, the Introduction should introduce those labels. The Discussion avoids them on purpose.
- **Methods 2.1, still wrong:** "115 per participant" should be 230 compatible and 230 incompatible. The sentence claiming R is "computed" contradicts Table 1: R is the raw response, and correctness is R = S.

**LaTeX:** write the quotes as ` ``negative'' `, the range as `11--41~ms`, and the values in math mode (`$z = 0.57$`).
