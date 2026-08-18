# [Bank Name] Statement Parsing Guide

<!--
This file was auto-learned. When you parse a statement from a bank that has no
guide yet, fill this out from what you see and save it as `<bank>.md` (lowercase,
no spaces — e.g. chase.md, bofa.md, wells-fargo.md). Update it whenever a new
pattern appears. The goal: next month this bank parses fast and consistently.
-->

## Overview
- **Bank:** [Full name]
- **Statement format:** [PDF / CSV], typically [N] pages, one per [statement cycle]
- **Confidence:** [High / Medium / Learning — how many statements this guide is based on]

## Layout & Structure
- **Header:** account holder, masked account number, statement period, beginning/ending balance
- **Transaction table columns (left→right):** [e.g. Date | Description | Amount | Balance]
- **Date format:** [MM/DD / Mmm DD / YYYY-MM-DD]
- **Footer:** [summary totals, contact details, page refs]

## Credit / Debit Convention
<!-- CRITICAL — how does this bank show money-in vs money-out? Get this right first. -->
- Money IN (credit / deposit): [e.g. separate "Deposits" column / positive value / "CR"]
- Money OUT (debit / withdrawal): [e.g. separate "Withdrawals" column / negative value]
- Overdraft / negative balance shown as: [convention]

## Transaction-Type Patterns
For each, note the description text this bank uses:
- **Payroll / income:** [pattern + typical date] (Direct Deposit, ACH credit)
- **Recurring ACH debits:** [pattern] (insurance, utilities, loan, subscriptions)
- **Card / POS purchases:** [pattern]
- **P2P transfers:** [pattern] (Zelle, Venmo, Cash App, PayPal)
- **Wires:** [pattern]
- **Internal transfers (own accounts):** [pattern] — exclude from spending
- **Bank fees:** [pattern] (monthly maintenance, overdraft, ATM)
- **ATM / cash withdrawals:** [pattern]
- **Checks / e-checks:** [pattern + check number]
- **Reversals / refunds:** [pattern] — net against original, don't double-count

## Category Mapping
| Category | Description patterns seen on this bank |
|---|---|
| Income | |
| Housing | |
| Utilities | |
| Groceries | |
| Transport / Gas | |
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
- [pending vs. posted, ACH timing, duplicate-looking lines, statement cycle not matching calendar month, etc.]

---
**Last updated:** [YYYY-MM-DD]
**Based on:** [N] statement(s)
