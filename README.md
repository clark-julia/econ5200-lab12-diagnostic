# econ5200-lab12-diagnostic
# Instrumental Variables: Weak Instruments, Compliers and the Exclusion Restriction

## Objective

I used simulated data and Card's (1995) college-proximity data to study when an instrumental variables estimate can be trusted, and when it cannot.

## Methodology

- Simulated data where the true effect of the treatment on the outcome was 1.0 and an unobserved confounder pushed OLS upward, so I knew the right answer.
- Changed the strength of the instrument and repeated the simulation 500 times at each strength, then compared the median 2SLS estimate with the median OLS estimate.
- Checked how often a statistically significant 2SLS estimate was still far from the true effect.
- Replicated Card's (1995) estimate of the return to schooling, using growing up near a four-year college as the instrument, with controls for experience and its square, race, region and metropolitan residence.
- Read the first-stage F alongside each 2SLS estimate before interpreting it.
- Gave the instrument a small direct effect on the outcome, which breaks the exclusion restriction, and measured how far the 2SLS estimate moved as that effect grew.
- Wrote my own two-stage least squares function from two OLS regressions and checked that it matched the linearmodels package.

## Key Findings

- With a very weak instrument (median first-stage F of 0.5), the median 2SLS estimate was 2.038, against a median OLS estimate of 1.998 and a true effect of 1.0. The 2SLS estimate moved toward OLS, not toward zero or toward the truth.
- A weak instrument does not give an obviously noisy answer. Many 2SLS estimates were statistically significant, and most of those were far from the true effect. A significant second stage does not show that the estimate is right.
- In the Card replication, the first-stage F was 16.7, the OLS return to schooling was 0.0740 and the 2SLS return was 0.1323. The F passes the usual rule of thumb, but it says nothing about whether the exclusion restriction holds.
- The 2SLS estimate applies to compliers, the men whose schooling changed because of where they grew up, not to everyone.
- A small direct effect of the instrument on the outcome moved the 2SLS estimate noticeably. The exclusion restriction cannot be tested, so I measured how large a violation the estimate can tolerate instead.
- My own two-stage least squares function matched linearmodels on the Card data.
