# Marketing A/B Test: Did the Ad Campaign Work?

**Users were randomly shown either an ad or a neutral public service announcement (PSA). Did the ads cause more purchases, by how much, and when do they work best?**

Statistical analysis of ~588K users from the Kaggle [Marketing A/B Testing](https://www.kaggle.com/datasets/faviovaz/marketing-ab-testing) dataset (Python).

![Conversion by group](ab_conversion.png)
![Dose response](ab_dose_response.png)
![Timing](ab_timing.png)

---

## Business questions
1. Did ads lift conversion compared with the PSA control, and is the result statistically significant?
2. How big is the effect in business terms (incremental conversions)?
3. Was the test large enough to detect a meaningful effect?
4. Does more exposure help, and which days and hours work best?

## Key findings
> Paste the numbers printed in section 7 of the notebook.

- **Result:** ads converted at [X]% vs [Y]% for PSA, a [+Z]% relative lift (p = [p]).
- **Confidence:** 95% CI for the lift: [low] to [high] percentage points.
- **Impact:** about [N] incremental conversions attributable to the ads.
- **Timing:** biggest lift on [day]; best hour [H]:00.
- **Exposure:** conversion rises with the number of ads seen (correlation, not proof of cause).

## Recommendations
1. **Keep the campaign running**: the lift is real and [large/small] relative to its cost (add cost data to calculate ROI).
2. **Shift budget toward [best day / hours]** and test reducing spend on [worst day].
3. **Run a follow-up test on frequency** (for example, a cap of 25 vs 50 ads) to see whether more exposure *causes* more sales.

## How to reproduce
1. Download `marketing_AB.csv` from the Kaggle link above (free account).
2. Open [`ab_test_analysis.ipynb`](ab_test_analysis.ipynb) in Google Colab, run all cells, and upload the CSV when asked.

## Methods
- Two-proportion z-test (pooled) and 95% confidence interval (unpooled) for the difference in conversion
- Minimum detectable effect at 80% power and 5% significance
- Incremental conversions = difference in conversion rate × users exposed
- Dose-response and day/hour breakdowns

## Limitations
- Average order value is **assumed** ($50) for the revenue estimate; real cost and revenue data would allow true ROI.
- Exposure (number of ads) isn't randomised, so dose-response is correlational.
- The groups are unequal by design (most users saw ads), which widens the control group's confidence interval.

## Tools
Python (Pandas, SciPy, Seaborn) · Google Colab · Statistics
