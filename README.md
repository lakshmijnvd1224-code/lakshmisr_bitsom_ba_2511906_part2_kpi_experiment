# Part 2: KPI Framework, Business Experiment Analysis & Decision Recommendation

**Student:** Lakshmi S R
**Student ID:** bitsom_ba_2511906
**Program:** BITSoM Business Analytics with Gen & Agentic AI
**Repository:** lakshmisr_bitsom_ba_2511906_part2_kpi_experiment

---

## Business Context

A subscription-based digital product company launched a new onboarding and activation campaign to improve user conversion. Users were randomly split into two groups — Control (existing onboarding) and Treatment (new campaign). The company wants to know whether the treatment should be launched to all users.

**Decision to be made:** Should the new campaign be rolled out to all users?
**Who it impacts:** New users, the business (revenue, support costs), and the product team.
**Evidence required:** Statistically significant improvement in paid conversion rate with no major degradation in guardrail metrics.

---

## Dataset Description

| Property | Details |
|---|---|
| File | campaign_experiment_data.xlsx |
| Total Records | 1,408 users |
| Control Group | 690 users (after removing 8 duplicates) |
| Treatment Group | 710 users (after removing 8 duplicates) |
| Columns | 16 (user_id, signup_date, experiment_group, region, device_type, traffic_source, plan_type, visited_landing_page, started_trial, completed_onboarding, converted_to_paid, revenue_30d, support_tickets_30d, refund_requested, days_to_convert, engagement_score) |
| Date Range | Feb 2025 – May 2025 |

---

## North Star Metric Selected

**Paid Conversion Rate** — the percentage of signed-up users who convert to a paying subscription.

**Why this is the North Star:**
- Directly measures the campaign's primary objective
- Every other metric in the funnel (visit rate, trial rate, onboarding) exists to drive this one number
- Connects directly to business revenue and growth
- Binary outcome making it statistically testable

**Risk of blind optimization:** Doubling conversion while cutting revenue per user in half and doubling support costs may not improve business outcomes — which is exactly what we observe in this experiment.

---

## KPI Tree Summary

```
PAID CONVERSION RATE (North Star)
├── Landing Page Engagement (Primary KPI 1)
│   ├── Landing Page Visit Rate
│   └── Traffic Source Quality
├── Trial & Onboarding (Primary KPI 2)
│   ├── Trial Start Rate
│   └── Onboarding Completion Rate
└── User Activation (Primary KPI 3)
    ├── Engagement Score
    └── Days to Convert

GUARDRAIL METRICS
├── Support Ticket Rate (must not increase)
├── Refund Rate (must stay near 0%)
└── Revenue per Converted User (must remain healthy)
```

---

## Experiment Analysis Approach

### Data Quality Checks (Task 4)
| Issue | Count | Action |
|---|---|---|
| Duplicate user_ids | 8 | Removed — kept first occurrence |
| Missing device_type | 18 | Excluded from device analysis |
| Missing traffic_source | 24 | Excluded from traffic analysis |
| Missing engagement_score | 14 | Excluded from engagement analysis |
| Missing days_to_convert | 1,336 | Expected — only converters have values |
| Revenue outliers (>500) | 38 | Noted and included with flag |

### Key Metrics Compared (Task 5)
All 11 required metrics computed for Control vs Treatment, plus segment breakdowns by Region, Device Type, Traffic Source, and Plan Type.

---

## Hypothesis Test Summary (Task 7)

| Parameter | Value |
|---|---|
| Test type | One-tailed Z-test for proportions |
| H₀ | Treatment conversion rate = Control conversion rate |
| H₁ | Treatment conversion rate > Control conversion rate |
| Significance level | 0.05 |
| Control conversion rate | 3.19% (22/690) |
| Treatment conversion rate | 7.04% (50/710) |
| Z-statistic | 3.2904 |
| P-value | 0.0005 |
| Decision | **REJECT H₀ — significant improvement confirmed** |

---

## Guardrail Metrics Considered (Task 8)

| Guardrail | Control | Treatment | Risk |
|---|---|---|---|
| Support Ticket Rate | 14.72% | 24.76% | HIGH — nearly doubled |
| Refund Rate | 0.00% | 0.42% | MEDIUM — new issue |
| Revenue per Converted User | 1,630.10 | 770.41 | HIGH — dropped 53% |

---

## Final Recommendation

** LAUNCH ONLY FOR SELECTED SEGMENTS**

- Launch for Premium and Basic plan users + Mobile users + Organic/Referral traffic
- Hold back from Free plan users and Paid Search traffic
- Investigate root cause of doubled support tickets before full launch
- Monitor 90-day retention for converted users

The conversion improvement is statistically significant and real. However, the guardrail signals are too concerning for a full launch without investigation.

---

## Assumptions and Limitations

1. Random assignment assumed — no verification of randomization quality performed
2. 30-day observation window may not capture long-term retention or churn
3. Revenue outliers (max: 8,610) included in averages — may skew revenue metrics
4. Novelty effect possible — treatment users may show higher engagement initially
5. Support ticket root cause unknown — could be onboarding confusion or product bugs

---

## Screenshots Included

| File | Shows |
|---|---|
| summary_metrics.png | Full Control vs Treatment metrics comparison table |
| hypothesis_test_output.png | Z-test inputs, calculations, and decision |
| kpi_tree_preview.png | KPI tree showing North Star, drivers, and guardrails |
