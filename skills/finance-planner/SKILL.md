---
name: Finance Planner
description: Monthly processing workflow. Scans statements, parses transactions, reconciles budget, updates debt balances, recalculates snowball, calculates interest burn, generates payment plan, updates dashboard, and writes monthly summary to archive.
triggers:
  - "process finances"
  - "monthly processing"
  - "update dashboard"
  - "parse statements"
  - "reconcile budget"
voice: "Direct, methodical, action-oriented. Tracks progress against baseline."
---

# Finance Planner — Monthly Processing Workflow

## Input Requirements

Before starting, verify these are present:
- Bank statements for all earners (PDF or CSV, from `statements/[earner]/[YYYY]/`)
- Creditor statements for all active debts (from `statements/loans/[earner]/`)
- Budget spreadsheet (`spreadsheets/FinPlan_v2.xlsx` with current month tab)
- References: `household-data.md`, `repayment-strategy.md`, `goal-plan.md` (if goals exist), `spending-baseline.md` (learned categories & averages), CHANGELOG, previous month summary

## Step 1: Inventory Statements

List what's available:

```
Statements Present:
- Alex Bank: ✓ (Jan, Feb, Mar) ✓ Complete
- Sam Bank: ✓ (Jan, Feb) ✗ Missing Mar
- Alex Creditor 1: ✓ Statement dated 2026-02-28
- Alex Creditor 2: ✗ No recent statement (estimate required)
- Sam Creditor: ✓ Statement dated 2026-02-28
```

Flag any missing items and note assumptions (e.g., "Estimating Alex Creditor 2 balance from last statement").

## Step 2: Parse Bank Statements

**First, find (or learn) the bank's parsing guide.** Look in `skills/country/[COUNTRY]/references/bank-parsing/` for a guide matching this statement's bank (e.g. `fnb.md`, `capitec.md`, `chase.md`).

- **Guide exists** → parse using it.
- **No guide for this bank (auto-learn)** → parse the statement carefully anyway (you can read any statement), then **create a new guide** at `skills/country/[COUNTRY]/references/bank-parsing/<bank>.md` using `_TEMPLATE.md` as the shape: capture the header layout, the transaction-description patterns (salary, debit orders, POS, transfers, fees, ATM, reversals), the credit/debit indicator, and the category mapping you used. Note the new guide in the CHANGELOG. Next month this bank parses fast and consistently instead of being re-figured from scratch.
- **Guide exists but the statement has new patterns** → parse, then append the new patterns to the guide and bump its "Last updated" line.

For each earner's bank statement:
1. Read statement using the bank guide (above) plus formatting rules from the country module (`skills/country/[COUNTRY]/SKILL.md`)
   - The country module provides currency format and category conventions; the bank guide provides that bank's format quirks
2. Extract: Date, Description, Amount
3. **Categorize using the learned merchant map** in `spending-baseline.md` (§1): if the merchant is already mapped (e.g. "Woolworths → Groceries"), reuse it — don't re-decide every month. If it's a **new merchant**, assign the best category and **add a row to the map** so it's learned for next time. Note new merchants in the month's summary.
4. Flag: Unusual transactions, out-of-category spending, duplicate entries
5. Summarize: Total in/out, major category totals

**Output format**:

```
Alex Bank — January 2026
Income:         +15,750 (salary)
Housing:        -4,200
Food:           -1,850
Transport:      -1,200
Utilities:      -1,100
Subscriptions:  -280 (Flag: New subscription)
Debt Payments:  -2,000
Other/Misc:     -850
Net:            +4,270

Total Receipts: 15,750
Total Spending: 11,480
```

## Step 3: Reconcile Budget vs. Actual

Compare parsed actuals to the budget in `FinPlan_v2.xlsx`:

```
Category        Budget    Actual    Variance    Flag
------------------------------------------------------
Housing        -4,200    -4,200    0%          ✓
Food           -1,800    -1,850    -3%         ✓
Transport      -1,200    -1,340    -12%        ⚠ Over budget
Utilities      -1,100    -1,080    +2%         ✓
Subscriptions  -150      -280      -87%        🚨 New item
Debt Payments  -2,000    -2,000    0%          ✓
```

Variance rule:
- ±5% = normal (✓)
- ±5-15% = investigate (⚠)
- >±15% = address (🚨)

### Update the Spending Baseline (learn over time)

After reconciling, update `spending-baseline.md` so the budget improves month over month:

1. **Category averages** — write this month's actual into each category row and recompute the **3-month and 6-month rolling averages**. Rolling averages smooth out one-off spikes (a big grocery month, an annual insurance debit).
2. **Budget-improvement suggestions** — where a category's rolling average has diverged from its budget for **2+ consecutive months** (not a single spike), suggest an adjustment: "Groceries has averaged R6,400 over 3 months vs R5,500 budget — raise the budget to ~R6,400, or investigate the drift." Persistent gaps mean the budget is wrong, not the spending.
3. **Confidence** — note how many months the baseline is built on (Learning → Improving → Stable). Early months are guidance; by month 3–4 the averages are trustworthy.

This is what turns a guessed onboarding budget into one grounded in how the household actually spends.

## Step 4: Update Debt Balances

For each active debt:
1. If creditor statement available: Use statement balance as of statement date
2. If no recent statement: Estimate using formula:
   - Previous balance - payments made + interest accrued
3. Document source: "Statement dated 2026-02-28" or "Estimated from 2026-01-31"

**Example**:
```
Alex Store Card (Target debt Phase 1)
- Previous balance (2026-01-31): 8,500
- Payments made (Feb):           -500
- Interest accrued (~2% monthly):  +170
- Current balance (2026-02-28):  8,170
```

Update `FinPlan_v2.xlsx` Debt Tracker tab.

## Step 5: Recalculate Snowball — run the projection script

Use the cascade simulator (do NOT hand-estimate the waterfall):

```
python3 ${CLAUDE_PLUGIN_ROOT}/skills/finance-planner/scripts/debt_projection.py \
    --xlsx spreadsheets/FinPlan_v2.xlsx --pool <realistic snowball> --reserve <standing diversions> \
    [--inject YYYY-MM:amount] [--divert YYYY-MM:permonth:target] [--include-vehicles] [--csv debts.csv]
```

- `--pool` = the household's CURRENT realistic snowball (from household-data.md); the script adds freed minimums automatically as debts die — never pre-add them.
- It reads balances/rates/minimums/priority from the Debt Tracker sheet (keep the Priority column = actual kill order) or a CSV.
- Output is a markdown milestone table + interest totals + minimums-only contrast + burn trajectory. Refresh the household's `archive/YYYY/debt_projection_*.md` with it.
- Compare to the previous run: name every projection row that became fact (coaching moment), investigate any date that slipped (slip months shift dates ~1:1).
- Scenarios worth running each time: base case; + known windfalls (`--inject`); + planned goal diversions (`--divert`).

**Output**:
```
Current Snowball (Phase 1 in progress)
Target: Alex Store Card (8,170 current, min payment $150)
Cascade: $500/month to target
Clearance: 18 months (by Aug 2027)

Next in cascade: Bank Credit Card (5,240)
Then: Sam Store Card (3,600)

Full payoff timeline: 48 months (by Mar 2030)
```

## Step 6: Calculate Interest Burn

Interest burn = total interest paid this month across all debts.

Formula per debt: `(Balance × Annual Rate) / 12`

Example:
```
Alex Store Card:  8,170 × 12% / 12 = 82/month
Bank Credit Card: 5,240 × 18% / 12 = 79/month
Sam Store Card:   3,600 × 15% / 12 = 45/month
Alex Auto:        25,000 × 7% / 12 = 146/month
Sam Car Loan:     50,000 × 6.5% / 12 = 271/month
-------
TOTAL INTEREST:   623/month

Baseline (Feb 2026): 650/month
Current vs Baseline: -4% (improving)
```

Track this monthly. Falling interest burn is a leading indicator of progress.

## Step 7: Generate Payment Plan

Split payment instructions by pay date if there are multiple earners. Fund both **debt**
(from `repayment-strategy.md`) and **goals** (the sinking-fund contributions from
`goal-plan.md`) — a debt-light, goal-heavy household will have little or no debt line and a
larger goal line, and that's correct. Format clearly:

```
MONTHLY PAYMENT PLAN — March 2026

Alex Salary (Last day of month)
  Available: 15,750
  Assigned:
    Housing:          4,200
    Food:             1,850
    Transport:        1,200
    Utilities:        1,100
    Subscriptions:    280
    Debt Minimum (CC): 75
    Debt Accelerator: 1,045 → Alex Store Card
    Goal contribution: 1,000 → Family holiday
  Balance:           5,000 (allocate to: emergency fund top-up or next earner's needs)

Sam Salary (Mid-month)
  Available: 9,200
  Assigned:
    Food contribution: 500
    Transport:        400
    Debt Minimum (TW): 150
    Debt Accelerator: 955 → Alex Store Card
    Goal contribution: 500 → Family holiday
  Balance:          6,195 (allocate to: housing/utilities)

Combined Debt Payments This Month: 2,225
- Alex Store Card (target): 2,000
- Other minimums: 225

Combined Goal Contributions This Month: 1,500
- Family holiday: 1,500 (→ separate savings/notice account, not the daily card)
```

## Step 8: Update Dashboard

Read `skills/finance-planner/references/dashboard-spec.md` for layout and styling.

Update `dashboards/progress_dashboard.pptx`:
- Debt freedom progress bar (use updated total debt) — omit or shrink if the household is debt-free
- Interest burn rate (current vs baseline)
- Debts cleared count (if any cleared this month)
- Current target debt name and balance
- **Goal progress bars** — one per active goal from `goal-plan.md` (saved / target, % complete, on-track-for-deadline flag). For a goal-focused household these are the headline, not the debt bar.
- **Spending trend** — top categories with their 3-month rolling average and direction (from `spending-baseline.md`)
- Next 3 milestones and projected dates (debt clears **and** goal target dates)
- Insurance coverage summary (from household-data.md)

**Milestone slide rule**: Create a new slide (Milestone Achieved) each time a debt is fully cleared **or a goal reaches its target**.

## Step 9: Write Monthly Summary

Create new file: `archive/YYYY/YYYY_MM_summary.md`

Template:

```markdown
# Monthly Summary — [Month Year]

## Actuals vs Budget
[Copy reconciliation table from Step 3]

## Debt Movement
[Previous balance → payments → interest → current balance for each debt]

## Goal Progress
[Per active goal: contributed this month → new balance → % to target → on track for deadline?]

## Progress Metrics
- Interest burn: [amount/month] (vs [baseline])
- Debt cleared this month: [yes/no]
- Snowball waterfall: On track / Ahead / Behind
- Goals: [on track / behind] for their deadlines
- Cash flow: [income - expenses = net]

## Spending Baseline
- New merchants learned: [list]
- Categories drifting from budget (2+ months): [list + suggested adjustment]
- Baseline confidence: [Learning / Improving / Stable]

## Top Opportunities This Month
[Any budget items > ±15% variance? Any missing income? Any new expenses?]

## Next Month Outlook
- Target debt: [Name and remaining balance]
- Expected clearance: [Month/Year]
- Next goal milestone: [Goal + target date]
- Key watch items: [Any risks or opportunities]

## Notes
[Any unusual transactions, income changes, or decisions made]
```

## Important Notes

- **Don't assume**: If a payment or transaction is unclear, ask or flag it
- **Source matters**: Always note whether debt balance is from statement or estimate
- **Timeline tracking**: Every month, compare payoff timeline to previous month; if it's slipping, investigate why
- **Country module**: Always use the appropriate country module for formatting and bank parsing rules
- **Keep it simple**: This is monthly processing, not deep analysis (that's money-mentor's job)

---

## Error Handling

**Missing statement**: Note assumption, estimate balance, flag for next month
**Over-budget category**: Note the variance; don't judgment, just report
**Income shortfall**: Adjust the cascade—which debt gets the hit?
**Unexpected credit**: Note it; update the cash flow; determine allocation
