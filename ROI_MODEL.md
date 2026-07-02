# Embers — ROI model

**All inputs are illustrative and labeled.** This is a decision model, not a forecast: it exists to show which variables matter, what the downside is bounded by, and what a pilot would need to validate. Real reply/conversion data (holdout-verified) replaces every assumption here within a quarter of running the program.

## Assumptions

| Input | Value (base) | Basis |
|---|---|---|
| Dormant closed-lost pool | 400 accounts | Illustrative — a mid-market B2B segment lost to timing/budget over ~18 months |
| Trigger a qualifying signal / year | 45% | Assumption; sensitivity-tested at 35–60% below |
| Gift-sent yield (enrichment + suppression pass) | 85% | Some accounts fail contact verification or hit suppression rules |
| Delivery rate | 95% | Address-validated physical sends |
| Delivered → meeting | 15% | Anchored: house-list direct mail responds at 5–9% (ANA/DMA Response Rate Report — see Sources); a relevant gift + a trigger-timed reason + coordinated rep follow-up is modeled at ~2x the top of that range. The single most sensitive input in the model. |
| Meeting → opportunity | 85% | These accounts already qualified once |
| Win rate | 25% | Mid-market B2B SaaS typically 20–28%; re-engagement of known contacts benchmarks higher (~37%, Champify 2025) — 25% stays under the benchmark deliberately |
| ACV | $30K | Illustrative mid-market industrial SaaS |
| Gift cost, all-in | $200 | Gift + shipping + platform transaction |
| Incremental tooling | $15K/yr | Gifting platform license; assumes CRM, enrichment, and call recording are already in the stack |

## Base-case funnel

```
400 dormant
  × 45% trigger        = 180 triggered
  × 85% sent yield     = 153 gifts sent      → gift spend ≈ $30.6K
  × 95% delivered      = ~145 delivered
  × 15% meeting        = ~22 meetings
  × 85% opp            = ~18 opportunities   → pipeline ≈ $540K
  × 25% win            = ~5 closed-won       → new ARR ≈ $140K
```

**Program cost ≈ $46K** (gifts ~$31K + tooling $15K)
**Year-one ARR ROI ≈ 3.0x · Pipeline ROI ≈ 12x · Cost per meeting ≈ $2.1K · Cost per closed-won ≈ $9.8K**

Against a $30K ACV on sticky multi-year contracts, cost-per-closed-won near $10K is the number that actually matters — year-one ARR is the deliberately conservative headline.

## Sensitivity — three scenarios

| | Conservative | Base | Aggressive |
|---|---|---|---|
| Trigger rate | 35% | 45% | 60% |
| Delivered → meeting | 10% | 15% | 22% |
| Win rate | 18% | 25% | 30% |
| ACV | $22K | $30K | $40K |
| **Meetings** | ~11 | ~22 | ~43 |
| **Closed-won** | ~2 | ~5 | ~11 |
| **New ARR** | ~$38K | ~$140K | ~$430K |
| **Pipeline** | ~$220K | ~$540K | ~$1.4M |
| **Program cost** | ~$39K | ~$46K | ~$56K |
| **Year-one ARR ROI** | ~1.0x | ~3.0x | ~7.7x |

The downside is bounded: spend scales with gifts actually sent (each behind a human approval gate), and the conservative case — every major input pessimistic at once — still roughly pays for itself in year one before any multi-year value.

## What a pilot must validate

1. **Delivered → meeting rate** — the swing variable. Modeled at 15%; the pilot measures it directly.
2. **Incrementality** — a 10–20% holdout (activated accounts that get no gift) separates lift the program *created* from deals that would have re-entered anyway. At this volume that's a quarterly read, not a weekly one; leading indicators (response rate by persona/gift/signal, SLA adherence) carry the weekly dashboard until the sample matures.
3. **Signal-type performance** — meetings booked by signal type, so low-converting signals get pruned and the scorer reweights on evidence.

## Sources

- [ANA Response Rate Report](https://www.ana.net/miccontent/show/id/rr-2024-02-ana-response-rate-report-2023) (Association of National Advertisers, formerly the DMA): direct mail to house lists responds at 5–9%, vs ~2–4.4% for prospect lists
- [Champify, "The Impact of Tracking Job Changes"](https://www.champify.io/resources/the-impact-of-tracking-job-changes-value-report): win rates on known-contact re-engagement ~37% vs ~19% cold baseline
- [SaaS win-rate benchmarks (Prospeo, data from 939 companies)](https://prospeo.io/s/saas-win-rate-benchmark): typical mid-market B2B SaaS win rates cluster in the 20–28% range
