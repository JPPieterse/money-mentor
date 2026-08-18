# [Bank Name] Statement Parsing Guide

<!--
This file was auto-learned. When you parse a statement from a bank that has no
guide yet, fill this out from what you see and save it as `<bank>.md` (lowercase,
no spaces — e.g. capitec.md, standard-bank.md). Update it whenever a new pattern
appears. The goal: next month this bank parses fast and consistently.
-->

## Overview
- **Bank:** [Full name]
- **Statement format:** [PDF / CSV], typically [N] pages, one per [calendar month / statement cycle]
- **Confidence:** [High / Medium / Learning — how many statements this guide is based on]

## Layout & Structure
- **Header:** account holder, masked account number, statement period, opening/closing balance
- **Transaction table columns (left→right):** [e.g. Date | Description | Amount | Balance]
- **Date format:** [DD/MM / DD Mmm / YYYY-MM-DD]
- **Footer:** [summary totals, contact details, page refs]

## Credit / Debit Convention
<!-- CRITICAL — how does this bank show money-in vs money-out? Get this right first. -->
- Money IN (credit): [e.g. "Cr" suffix / separate column / positive value]
- Money OUT (debit): [e.g. no suffix / separate column / negative value]
- Negative/overdraft balance shown as: [convention]

## Transaction-Type Patterns
For each, note the description text this bank uses:
- **Salary / income:** [pattern + typical date]
- **Debit orders / standing orders:** [pattern] (insurance, utilities, loan, subscriptions)
- **Card / POS purchases:** [pattern]
- **Manual transfers / payments:** [pattern]
- **Internal transfers (own accounts):** [pattern] — exclude from spending
- **Bank fees:** [pattern]
- **ATM / cash withdrawals:** [pattern]
- **Reversals / refunds:** [pattern] — net against original, don't double-count
- **[Bank-specific, e.g. rewards, instant-money, e-wallet]:** [pattern]

## Category Mapping
| Category | Description patterns seen on this bank |
|---|---|
| Income | |
| Housing | |
| Utilities | |
| Groceries | |
| Transport / Fuel | |
| Insurance | |
| Debt repayments | |
| Dining / Entertainment | |
| Savings / Goal contributions | |
| Bank fees | |

## Example Snippet
```
[paste a few anonymised lines showing the columns and a credit + a debit]
```

## Parsing Notes / Gotchas
- [anything that tripped you up: timing of debit orders, duplicate-looking lines, mid-month cycles, etc.]

---
**Last updated:** [YYYY-MM-DD]
**Based on:** [N] statement(s)
