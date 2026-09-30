# 4 Discussion

In this report we examined whether in-group favouritism produced by attitude priming is larger than out-group derogation. We compared the accuracy and response times (RT) of 12 Caucasian participants classifying positive and negative words after a white (in-group) or black (out-group) face prime, and fitted a DDM in which the starting point depends on the face. Overall, participants answered correctly on 72.5% of the trials with an average RT of 0.56 seconds. They made significantly more errors on incompatible trials, and while correct responses were faster on compatible trials, errors were faster on incompatible trials. **[DDM – TBD: fitted starting points after in-group and out-group faces relative to the midpoint.]**

The compatibility effect replicates the attitude priming findings of Fazio et al. (1995): in-group faces facilitate positive and out-group faces negative classifications, even though the faces were irrelevant to the task. This supports the view that such attitudes are activated automatically (Fazio et al., 1986; Greenwald & Banaji, 1995). The RT pattern is also informative about the mechanism. If the prime only lowered the drift rate on incompatible trials, both correct and error responses would be slower on those trials. Instead, responses in the direction of the prime were fast whether they were correct or not, which is the signature of a starting point lying closer to the prime-congruent threshold (White & Poldrack, 2014), in line with Todd et al. (2021). **[DDM – TBD: whether the in-group shift from the midpoint exceeds the out-group shift, i.e. whether favouritism outweighs derogation as expected from Brewer (1999).]** Finally, slower participants were not more accurate (Figure 1), suggesting individual differences in drift rate rather than in response caution.

Our analysis has several limitations. First, the sample is small and consists only of Caucasian participants, so we cannot test whether the bias is reciprocal, as Fazio et al. (1995) found for black participants. Second, the dataset contains no neutral prime condition. Comparing the starting point to the midpoint therefore assumes that participants have no general preference for one response; a general tendency to answer "positive" would inflate the estimated in-group favouritism and hide out-group derogation. Third, trial order and item identity are not recorded, so learning, fatigue and item effects could not be modelled. Fourth, the statistical tests used per-subject means of untrimmed RTs, and with 460 trials per participant spread over four face-word combinations and few errors per combination, per-subject DDM estimates may be unreliable. Lastly, our model only lets the face change the starting point, while primes might also affect the drift rate or the non-decision time.

Future work could include a neutral baseline prime, such as a scrambled face, to estimate the neutral starting point directly instead of assuming it. Recruiting black participants and a larger sample would allow testing whether the asymmetry between favouritism and derogation holds for both groups. A hierarchical Bayesian DDM (Wiecki et al., 2013) would make better use of the limited trials per participant, and formally comparing models in which the face affects the starting point, the drift rate, or both would test whether the bias is truly a response bias.

---

## Notes (not part of the section)

**Word count:** ~490 words of body text excluding the two **[DDM – TBD]** placeholders. Those two placeholders get ~40 words once the DDM results are in, so a few words will need trimming elsewhere to stay under 500 (the individual-differences sentence at the end of paragraph 2 is the easiest cut).

**To update once the DDM part is finished:**

- Fill in the two **[DDM – TBD]** placeholders with the fitted starting points (in-group vs. out-group, distance from 0.5).
- Check the limitations still match the final model: if the fit also frees drift rate / non-decision time per face, or if RTs get trimmed before fitting, edit the last two limitations accordingly.
- If the fit is pooled rather than per subject, change "per-subject DDM estimates" in the fourth limitation.

**New references to add to the reference list** (same style as the existing ones):

- White, C. N., & Poldrack, R. A. (2014). Decomposing bias in different types of simple decisions. _Journal of Experimental Psychology: Learning, Memory, and Cognition_, _40_, 385-398. doi: 10.1037/a0034851
- Wiecki, T. V., Sofer, I., & Frank, M. J. (2013). HDDM: Hierarchical Bayesian estimation of the drift-diffusion model in Python. _Frontiers in Neuroinformatics_, _7_, 14. doi: 10.3389/fninf.2013.00014

```bibtex
@article{white2014decomposing,
  author  = {White, Corey N. and Poldrack, Russell A.},
  title   = {Decomposing bias in different types of simple decisions},
  journal = {Journal of Experimental Psychology: Learning, Memory, and Cognition},
  year    = {2014},
  volume  = {40},
  number  = {2},
  pages   = {385--398},
  doi     = {10.1037/a0034851}
}

@article{wiecki2013hddm,
  author  = {Wiecki, Thomas V. and Sofer, Imri and Frank, Michael J.},
  title   = {{HDDM}: Hierarchical {B}ayesian estimation of the drift-diffusion model in {P}ython},
  journal = {Frontiers in Neuroinformatics},
  year    = {2013},
  volume  = {7},
  pages   = {14},
  doi     = {10.3389/fninf.2013.00014}
}
```
