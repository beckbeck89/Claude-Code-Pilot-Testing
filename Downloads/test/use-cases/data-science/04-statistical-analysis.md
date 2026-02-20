# Use Case: Statistical Analysis

## Objective

Ask the AI tool to perform a rigorous statistical analysis including hypothesis testing, confidence intervals, and appropriate test selection. Tests whether the tool applies statistics correctly and communicates results accurately.

## The Task

You're analyzing the results of an A/B test for a website redesign. Generate or use the following scenario:

### Scenario

An e-commerce site ran an A/B test on their checkout page for 4 weeks:
- **Control (A)**: Original checkout design — 5,000 visitors, 312 conversions
- **Treatment (B)**: New streamlined design — 4,800 visitors, 336 conversions

Additional data per group: average order value, time on page, and bounce rate (generate realistic sample data for these).

### Analysis Required

1. **Conversion rate comparison**: Is the difference statistically significant?
2. **Appropriate test selection**: Choose and justify the right statistical test
3. **Effect size**: Calculate practical significance (not just p-values)
4. **Confidence intervals**: For the difference in conversion rates
5. **Power analysis**: Was the sample size sufficient?
6. **Revenue impact analysis**: Compare average order values between groups
7. **Multiple comparisons**: If testing multiple metrics, address the multiple testing problem
8. **Recommendation**: Clear business recommendation based on the analysis

## Acceptance Criteria

- [ ] Correct statistical test chosen and justified (e.g., chi-square, z-test for proportions)
- [ ] P-value calculated correctly
- [ ] Confidence interval computed and interpreted correctly
- [ ] Effect size reported (Cohen's h or similar)
- [ ] Power analysis included
- [ ] Results interpreted correctly (no common mistakes like "p > 0.05 means no difference")
- [ ] Business recommendation is sound and follows from the analysis

## Suggested Prompt

> "Analyze this A/B test data. Control: 5000 visitors, 312 conversions. Treatment: 4800 visitors, 336 conversions. Determine if the new design is significantly better. Include appropriate hypothesis tests, effect sizes, confidence intervals, and a power analysis. Give me a clear business recommendation."

## What to Observe

- Does it choose the right test (proportion z-test or chi-square)?
- Does it state hypotheses correctly (H0, H1)?
- Does it interpret p-values correctly (not "proves" or "no effect")?
- Does it go beyond p-values to practical significance?
- Does it address assumptions of the chosen test?
- Is the power analysis correct?
- Does it communicate results in business-friendly language?
- Does it caution about limitations (e.g., novelty effect, seasonality)?
