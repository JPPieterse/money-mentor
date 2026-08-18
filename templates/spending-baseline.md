# Spending Baseline — Learned Categories & Averages

Last updated: [DATE]

<!--
This file is the household's learned spending memory. Finance Planner maintains it
every month:
  1. MERCHANT MAP — remembers which merchant belongs in which category, so you don't
     re-decide "Woolworths = Groceries" every month. New merchant → add a row.
  2. CATEGORY AVERAGES — rolling average of actual spend per category, so the budget
     drifts toward reality instead of a guess made at onboarding.
  3. BUDGET SUGGESTIONS — where the rolling average has diverged from the budget,
     propose an adjustment.
Confidence rises as more months are logged.
-->

## 1. Merchant → Category Map (learned)

<!-- Add a row the first time a merchant appears. Match on the description stem the
bank prints, not the full noisy string. -->

| Merchant / description stem | Category | Notes |
|-----------------------------|----------|-------|
| [Pick n Pay / Woolworths / Checkers] | Groceries | |
| [Shell / Engen / BP] | Transport / Fuel | |
| [Netflix / Spotify] | Subscriptions | |
| [Discovery / Hollard] | Insurance | |
| [Uber / Bolt] | Transport | |
| [pharmacy / Clicks / Dischem] | Healthcare | |
| [restaurant / takeaway names] | Dining & Entertainment | |
| [transfer to savings/notice acct] | Savings / Goal contributions | exclude from spending totals |

## 2. Category Rolling Averages

<!-- Update each month from the reconciled actuals. Keep last-3-month and last-6-month
averages; they smooth out one-off spikes. -->

| Category | This month | 3-mo avg | 6-mo avg | Trend |
|----------|-----------|----------|----------|-------|
| Groceries | [amount] | [amount] | [amount] | [↑/↓/→] |
| Transport / Fuel | [amount] | [amount] | [amount] | |
| Dining & Entertainment | [amount] | [amount] | [amount] | |
| Utilities | [amount] | [amount] | [amount] | |
| Healthcare | [amount] | [amount] | [amount] | |
| Subscriptions | [amount] | [amount] | [amount] | |
| Personal care | [amount] | [amount] | [amount] | |
| Other / Misc | [amount] | [amount] | [amount] | |

## 3. Budget-Improvement Suggestions

<!-- Generated from average-vs-budget divergence. Only flag persistent gaps (2+ months),
not single spikes. -->

| Category | Budget | 3-mo avg | Gap | Suggestion |
|----------|--------|----------|-----|------------|
| [e.g. Groceries] | [amount] | [amount] | [+/−] | [raise/lower budget to ~X, or investigate] |

## Notes

- New merchants learned this month: [list]
- Re-categorisations / corrections: [list]
- Confidence: [Learning / Improving / Stable — based on N months logged]
