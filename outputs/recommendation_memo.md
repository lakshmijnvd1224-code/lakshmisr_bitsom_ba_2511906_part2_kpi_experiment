# Recommendation Memo
## Campaign Experiment Analysis — Decision Recommendation
**To:** Leadership Team
**From:** Lakshmi S R, Business Analyst
**Student ID:** bitsom_ba_2511906
**Date:** 2026-06-22
**Subject:** Should we launch the new onboarding campaign to all users?

---

## Executive Summary

The new onboarding campaign significantly improves paid conversion rate (3.19% → 7.04%, p=0.0005). However, three guardrail metrics raise serious concerns — support ticket rate nearly doubled, revenue per converted user dropped by 53%, and refunds appeared. **Recommendation: Do not launch to all users yet. Launch only to Premium and Basic plan users while investigating the support and revenue quality issues.**

---

## 1. North Star Metric

**Paid Conversion Rate** — the percentage of signed-up users who convert to a paying subscription.

This is the North Star because it directly measures the campaign's core objective (convert users to paid) and connects every other metric in the funnel to business revenue.

| Group | Users | Conversions | Conversion Rate |
|---|---|---|---|
| Control | 690 | 22 | 3.19% |
| Treatment | 710 | 50 | 7.04% |
| **Improvement** | | **+28 conversions** | **+3.82 percentage points** |

---

## 2. KPI Tree Summary

The KPI tree maps how Paid Conversion Rate breaks down:

**Primary Drivers:**
- Landing Page Engagement → Visit Rate + Traffic Source Quality
- Trial & Onboarding → Trial Start Rate + Onboarding Completion Rate
- User Activation → Engagement Score + Days to Convert

**Guardrail Metrics:**
- Support Ticket Rate (must not increase)
- Refund Rate (must stay near 0%)
- Revenue per Converted User (must remain healthy)

---

## 3. Experiment Result Summary

| Metric | Control | Treatment | Change | Status |
|---|---|---|---|---|
| Landing Page Visit Rate | 63.64% | 72.59% | +8.95pp | Improved |
| Trial Start Rate | 25.11% | 29.09% | +3.98pp | Improved |
| Onboarding Completion Rate | 15.58% | 21.26% | +5.68pp | Improved |
| **Paid Conversion Rate** | **3.19%** | **7.04%** | **+3.85pp** | **North Star improved** |
| Avg Revenue per User | 51.75 | 53.88 | +4.1% | Slightly improved |
| Avg Revenue per Converted User | 1,630.10 | 770.41 | -52.7% | Major drop |
| Refund Rate | 0.00% | 0.42% | +0.42pp | New issue |
| Support Ticket Rate | 14.72% | 24.76% | +10.04pp | Major increase |
| Avg Engagement Score | 57.03 | 62.93 | +10.3% | Improved |
| Avg Days to Convert | 8.86 | 6.40 | -27.8% | Faster |

---

## 4. Hypothesis Test Interpretation

- **Test:** One-tailed Z-test for proportions
- **H₀:** Treatment conversion rate = Control conversion rate
- **H₁:** Treatment conversion rate > Control conversion rate
- **Z-statistic:** 3.2904
- **P-value:** 0.0005
- **Decision:** REJECT H₀ at α = 0.05

**The improvement in conversion rate is statistically significant at 99.9% confidence.** This is not random chance — the campaign genuinely improves conversion.

---

## 5. Guardrail Analysis

### Guardrail 1 — Support Ticket Rate HIGH RISK
- Control: 14.72% → Treatment: 24.76% (+10.04 percentage points)
- Nearly doubled — indicates treatment users are confused or experiencing friction
- This increases operational costs significantly
- **Risk level: HIGH**

### Guardrail 2 — Refund Rate MEDIUM RISK
- Control: 0.00% → Treatment: 0.42%
- Refunds appeared in treatment group where none existed before
- Suggests some users are converting but not finding value
- **Risk level: MEDIUM**

### Guardrail 3 — Revenue per Converted User HIGH RISK
- Control: ₹1,630.10 → Treatment: ₹770.41 (-52.7%)
- Treatment doubled conversions but revenue per converter halved
- Total revenue barely moved (₹51.75 → ₹53.88 per user)
- The campaign may be attracting lower-value users
- **Risk level: HIGH**

---

## 6. Segment-Level Insights

**By Region:**
- All 4 regions show conversion improvement in Treatment
- North region has the largest treatment effect
- No region shows a decline — positive signal

**By Device:**
- Mobile users show the strongest conversion improvement
- Desktop users show modest improvement
- Treatment appears most effective for mobile users

**By Plan Type:**
- Premium and Basic plan users show strong conversion improvement
- Free plan users show smaller improvement
- Suggests campaign resonates better with users who intended to pay

**By Traffic Source:**
- Organic and Referral traffic sources show strongest improvement
- Paid Search shows mixed results on revenue quality

---

## 7. Final Recommendation

### LAUNCH ONLY FOR SELECTED SEGMENTS

**Do not do a full launch yet.** Instead:

1. **Launch immediately for:**
   - Premium and Basic plan users (strong conversion + better revenue quality)
   - Mobile device users (highest conversion improvement)
   - Organic and Referral traffic sources

2. **Hold back from:**
   - Free plan users (lower revenue quality in treatment)
   - Paid Search traffic (revenue quality concerns)

3. **Investigate before full launch:**
   - Why did support tickets nearly double? Identify the friction point
   - Why did revenue per converted user drop by 53%? Pricing or plan selection issue?
   - Are refunds concentrated in a specific segment?

---

## 8. Risks and Limitations

| Risk | Description |
|---|---|
| Support cost increase | 10pp increase in support tickets significantly raises operational costs |
| Revenue quality | Converting more users at lower revenue may not improve business outcomes |
| Refund trend | 0.42% refund rate is small now but could grow with full launch |
| Short observation window | Only 30 days of data — long-term retention unknown |
| Novelty effect | Treatment users may be more engaged initially but churn later |

---

## 9. Next Steps

1. **Week 1-2:** Investigate root cause of doubled support tickets
2. **Week 2-3:** Segment launch for Premium + Basic + Mobile users
3. **Week 4-6:** Monitor revenue quality and refund rate in launched segments
4. **Week 6-8:** If guardrails stabilize, proceed to broader launch
5. **Week 8+:** Re-run experiment with improved campaign addressing support issues
6. **Ongoing:** Track 90-day retention for converted users to measure long-term value
