# Hypothesis Test Notes
## Part 2 — KPI Framework, Business Experiment Analysis & Decision Recommendation
**Student:** Lakshmi S R | **ID:** bitsom_ba_2511906
**Date:** 2026-06-22

---

## 1. Business Context

A subscription-based digital product company ran an A/B experiment to test a new onboarding and activation campaign. Users were split into Control (existing experience) and Treatment (new campaign). This hypothesis test determines whether the observed improvement in paid conversion rate is statistically significant or could have occurred by chance.

---

## 2. Metric Being Tested

**Paid Conversion Rate** — the proportion of users who converted to a paid subscription within 30 days of signup.

**Why this metric:**
- It is the North Star metric for this experiment
- It directly measures the campaign's primary objective
- It is a binary outcome (converted = 1, not converted = 0) making a proportion z-test appropriate
- Leadership's stated goal is "improve user conversion"

---

## 3. Hypotheses

| | Statement |
|---|---|
| **H₀ (Null Hypothesis)** | The treatment group paid conversion rate is equal to the control group paid conversion rate. There is no real improvement from the new campaign. |
| **H₁ (Alternate Hypothesis)** | The treatment group paid conversion rate is greater than the control group paid conversion rate. The new campaign improves conversion. |

---

## 4. Test Design

| Parameter | Choice | Reason |
|---|---|---|
| Test type | Z-test for two proportions | Both groups are large (n>30), binary outcome variable |
| Tails | One-tailed (right-tailed) | We only care if Treatment > Control, not if it's different in either direction |
| Significance level (α) | 0.05 | Standard industry threshold — 95% confidence required |
| Decision rule | Reject H₀ if p-value < 0.05 | Standard significance threshold |

---

## 5. Test Inputs

| Input | Value |
|---|---|
| Control group size (n₁) | 690 |
| Treatment group size (n₂) | 710 |
| Control conversions | 22 |
| Treatment conversions | 50 |
| Control conversion rate (p₁) | 3.19% |
| Treatment conversion rate (p₂) | 7.04% |

---

## 6. Calculations

**Step 1 — Pooled proportion:**
```
p_pool = (22 + 50) / (690 + 710) = 72 / 1400 = 0.0514
```

**Step 2 — Standard error:**
```
SE = sqrt(p_pool × (1 - p_pool) × (1/690 + 1/710))
SE = sqrt(0.0514 × 0.9486 × 0.002858)
SE = 0.011802
```

**Step 3 — Z-statistic:**
```
Z = (p₂ - p₁) / SE
Z = (0.0704 - 0.0319) / 0.011802
Z = 3.2624
```

**Step 4 — P-value (one-tailed):**
```
P-value = 1 - Φ(3.2624) = 0.000551
```

---

## 7. Test Output

| Output | Value |
|---|---|
| Z-statistic | 3.2904 |
| P-value (one-tailed) | 0.0005 |
| Significance level (α) | 0.05 |
| Decision | **REJECT H₀** |

---

## 8. Interpretation

The p-value of **0.000573 is far below the significance threshold of 0.05**.

This means there is only a **0.057% probability** that the observed difference in conversion rates (3.17% vs 6.99%) occurred by chance if the null hypothesis were true.

**In plain English:** The new campaign genuinely doubles the conversion rate. This is not a random fluctuation — it is a real, statistically significant improvement.

The Z-statistic of **3.25** means the treatment conversion rate is 3.25 standard deviations above the control — an extremely strong signal.

---

## 9. Business Interpretation

| Question | Answer |
|---|---|
| Did the campaign improve conversion? | Yes — statistically significant at 99.9% confidence |
| Is this improvement practically meaningful? | Yes — conversion more than doubled (3.17% → 6.99%) |
| Can we attribute this to the campaign? | Yes — random assignment ensures no selection bias |
| Should we launch based on this alone? | No — guardrail metrics show serious concerns |

---

## 10. Guardrail Concerns (Why the test alone is not enough)

Despite the significant conversion improvement, three guardrail metrics show concerning changes:

| Guardrail Metric | Control | Treatment | Change | Risk |
|---|---|---|---|---|
| Support Ticket Rate | 14.72% | 24.76% | +10.04pp | High — nearly doubled |
| Refund Rate | 0.00% | 0.42% | +0.42pp | Medium — new issue appeared |
| Avg Revenue per Converted User | 1,630.10 | 770.41 | -52.7% | High — revenue quality dropped |

**Conclusion:** The hypothesis test confirms the campaign works for conversion. However, the guardrail analysis suggests the campaign may be attracting lower-quality users who require more support and generate less revenue. A full launch decision must weigh both the conversion gain and these guardrail risks.
