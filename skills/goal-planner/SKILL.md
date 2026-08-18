---
name: Goal Planner
description: Turns a named goal with a deadline (a move, a car, a holiday, a house deposit, a wedding, school fees) into a monthly sinking-fund contribution, tracks progress, and sequences it sensibly against debt payoff and the emergency fund. For people whose main financial job is saving toward something, not just clearing debt.
triggers:
  - "goal planner"
  - "save for"
  - "saving toward"
  - "sinking fund"
  - "how do we afford"
  - "how much do I need to save"
  - "planning a holiday"
  - "new car"
  - "house deposit"
  - "moving"
  - "wedding"
  - "big purchase"
  - "savings goal"
voice: "Direct, warm, practical. Treats a goal as a plan with a number and a date, not a wish. Never makes someone feel bad for wanting the thing."
---

# Goal Planner — Sinking Funds for Named Goals

A goal is a target amount by a target date. This skill turns each one into a monthly
put-away, tracks the running balance, and works out where it sits alongside debt and the
emergency fund. This is the room for the person whose financial life is "fund the move,
then the car, then the holiday" — not everyone walks in carrying debt.

## Step 1: Load Household Context

Read:
- `references/household-data.md` — income, expenses, debts, buffer, and the **Goals** table (the master list of goals)
- `references/goal-plan.md` — the household's own sequenced goal plan, if it exists (it overrides the generic sequencing below)
- `references/repayment-strategy.md` — debt cascade and timeline (goals share cash flow with debt)
- CHANGELOG + latest archive summary — recent progress, any goal already funded

Read the country module for currency formatting and the right cash instruments:
`skills/country/[COUNTRY_CODE]/SKILL.md`.

## Step 2: Capture / Refresh Each Goal

For every goal, pin down:
- **Name** (e.g. "House deposit")
- **Target amount** (research a realistic number if they only have a vague one)
- **Deadline** (a real month/year)
- **Saved so far**
- **Priority** (which goal wins if cash is tight)

## Step 3: Do the Sinking-Fund Maths

For each goal:
```
Monthly contribution = (Target − Saved so far) ÷ Months until deadline
```
Then sanity-check the **total** goal contributions against free cash flow:
```
Free cash = Income − fixed expenses − debt minimums − buffer − conscious spending
```
- If total goal put-aways fit inside free cash → good, lock them in.
- If they don't → the deadline, the target, or the priority has to give. Show the trade-off
  honestly ("to hit the move by March you'd need R6.4k/mo, but only R4k is free — either
  push the date to July, trim the target, or pause the lowest-priority goal").

## Step 4: Sequence Against Debt & Safety (meet them where they are)

Goals are not strictly "after debt." Sequence like this:

1. **Emergency-fund floor first** — at least 1 month of expenses before aggressive goal saving; a goal fund is not an emergency fund.
2. **High-interest debt keeps priority for the bulk** — no sinking fund beats paying down debt above ~15–20%. But fund at least the most important dated goal in parallel at a sustainable level, or the plan gets abandoned. A little progress on the thing they actually care about is what keeps them in the game.
3. **Dated goals under ~24 months → cash, not the market.** Money needed soon does not belong in equities. Use a separate savings/notice/money-market account — boring, liquid, and not linked to the daily card. (Mirror Wealth Builder Phase 2.)
4. **Debt-free, goal-heavy household** → goals become the main event; fund them fully, then push surplus to Wealth Builder.

## Step 5: Write It Down & Hand Off Execution

- **Update the Goals table** in `references/household-data.md` with each goal's monthly contribution and saved-so-far.
- **Generate / update `references/goal-plan.md`** from `templates/goal-plan.md` — the sequenced plan with per-goal maths and target dates.
- **Execution is monthly and lives in Finance Planner.** Each goal's contribution becomes a
  **"Goal contributions"** line in the monthly payment plan, and progress shows on the
  dashboard. Goal Planner sets the plan; Finance Planner runs it each month — the same split
  debt uses (repayment-strategy.md defines, Finance Planner executes).

## Step 6: Answer the Actual Question

Anchor to their numbers:
- "Can we afford the move by [date]?" → contribution needed vs. free cash; give the honest verdict.
- "Should I save for the car or kill the credit card first?" → Step 4 sequencing on their real rates.
- "Where do I keep this money?" → Step 4 point 3 + country module cash instruments.

## Disclaimer

*I'm not a licensed financial advisor. This is a savings plan built from general principles
and your own recorded numbers. For big commitments (property, vehicle finance), confirm the
details with a qualified adviser in your country.*

---

## Response Template

```
# Goal Plan — [Date]

## Goals
| Goal | Target | Deadline | Saved | Monthly needed | Priority |
|------|--------|----------|-------|----------------|----------|
| [name] | [amount] | [Mmm YYYY] | [amount] | [amount] | [1..n] |

## Fit Check
Free cash/month: [amount]
Total goal put-aways: [amount]  → [fits / over by X]

## Sequencing
[Where goals sit vs. debt and emergency fund, on their actual rates/dates]

## This Month
- [Goal contributions to make — hands to Finance Planner]

## Verdict
[Direct answer: on track / adjust date / adjust target / re-prioritise]

---
*I'm not a licensed financial advisor...*
```
