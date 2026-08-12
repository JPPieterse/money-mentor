---
name: money-mentor-za
description: South Africa financial context module for Money Mentor. ZAR formatting, tax-advantaged accounts (TFSA, RA, two-pot), NCA debt rules, SA banking landscape, estate basics, and realistic SA interest-rate context.
status: active
---

# Money Mentor: South Africa Module

> **⚠ Numbers live in `references/tax-and-accounts.md`** (last verified 10 Jun 2026). This file is the qualitative map. Rates, brackets and limits change every Budget (late Feb) — verify on www.sars.gov.za before relying on them.

## Currency & Formatting

- **Currency:** South African Rand (ZAR) — format **R1,234.56** (no space after R).
- Tax year: 1 March – end February, named by END year ("2027 tax year" = Mar 2026–Feb 2027).
- Loaded when `household-data.md` has `Country: ZA`.

## Tax-Advantaged Accounts (details + current limits → tax-and-accounts.md)

- **TFSA:** R46,000/tax year (from Mar 2026), R500,000 lifetime, 40% penalty on excess. Limits run per TAX year, withdrawals never restore room, move providers only via official transfer.
- **Retirement funds (RA/pension/provident):** deduct 27.5% of the greater of remuneration/taxable income (cap R430,000 from Mar 2026; excess carries forward). **Two-pot system** since Sep 2024: 1/3 savings pot (one withdrawal/tax year, taxed at marginal rate — emergency-only money), 2/3 retirement pot (locked, annuitised).
- **Retirement lump sum:** R550,000 tax-free is LIFETIME CUMULATIVE across all funds — not per product.
- Typical priority for spare rand AFTER high-interest debt: employer match (if any) → TFSA (equity ETFs) → RA top-up for the tax deduction (especially at 31%+ marginal rates) → discretionary.

## National Credit Act — the rules that actually matter

1. **Settlement:** ≤R250k original = settle anytime, no penalty. >R250k (vehicles, bonds) = give 3 months' written notice or face up to ~3 months' interest as termination charge. Always work off a written settlement quote (valid 5 business days).
2. **s129 default notice** must precede legal action — never ignore it.
3. **Statutory in duplum (s103(5)):** once in default, interest + fees + costs are capped at the outstanding balance at default — defaulted debts can at most double.
4. **Prescription:** unsecured debt dies after 3 years without payment/acknowledgement/summons. Any payment restarts the clock; never acknowledge old "ghost" debt before checking prescription.
5. **Debt review (s86)** = statutory protection but locks out new credit until a clearance certificate; treat as last resort.
6. **Credit life insurance** on NCA loans is fee-capped and substitutable — audit it on every loan (cancelling overpriced credit life and substituting a compliant policy routinely saves R100–600/mo).

## Banking Landscape

- **Big 4:** FNB (strong app/eBucks, premium fees R100–600/mo on bundled accounts), Standard Bank, Absa, Nedbank.
- **Low-cost challengers:** Capitec (full-feature, ±R7/mo), TymeBank (near-free, digital-only), Discovery Bank (rewards-led), Bank Zero. A bundled-account household can often save R300–600/mo switching — weigh rewards honestly (eBucks etc. mostly reward spending you shouldn't inflate).
- Statements: see `references/bank-parsing/fnb.md` for FNB transaction patterns.

## Common Debt Types — realistic SA pricing (verify per statement; repo-linked caps)

| Type | Typical real-world rate | Notes |
|---|---|---|
| Payday/short-term loans (Wonga, bank "cash advance" products) | up to ~5%/MONTH | Wealth destroyers. A R1,500 loan costing R224 for 5 days ≈ 1,000%+ annualised. Break the pattern structurally (between-pays float). |
| Unsecured personal loans | 18–29% | Bank or non-bank; NCA cap ≈ repo + 21%. |
| Store cards (Truworths, Mr Price, PnP, Edgars) | ~20–25% | Watch the add-ons: "account protection", club fees, lost-card fees keep billing even on R0 balances — cancel explicitly when an account is paid off. |
| Credit cards | ~14–21% | Interest-free up to ~55 days only if paid IN FULL. |
| Vehicle finance (WesBank, MFC, Absa AVAF) | prime ± a few % | Balloons of 30–40% are common — plan a sinking fund or refinance early. >R250k originals: 3-month NCA notice to settle. |
| Bonds/home loans | around prime | — |

## Insurance & Medical

- **Medical aid ≠ medical insurance.** Scheme membership earns fixed-rand s6A tax credits (NOT a % of contributions). GEMS for government employees; Discovery/Bonitas/Momentum in the open market.
- Comprehensive vehicle cover is voluntary (no compulsory third-party regime like UK/AU) — being uninsured on a financed car breaches the finance agreement.
- Group life via employer + standalone term life: cheap relative to credit life; check cover = 10–12× income against the estate plan.

## Estate Quick Notes (full details → tax-and-accounts.md → estate-planning skill)

- Estate duty 20%/25% over R30M; R3.5M abatement, portable between spouses; s4(q) spouse deduction.
- **s37C:** retirement fund death benefits are distributed by trustees to dependants — your nomination is not binding. Life policies pay beneficiaries directly (no executor fee).
- **Marriage regime drives everything:** in community of property = shared estate AND shared debt liability + spousal consent rules for credit. Establish the regime FIRST in any SA estate or debt-liability conversation.
- Wills: 2 non-beneficiary witnesses, every page signed; name executor + fee arrangement; guardianship nomination for minors.

## When working with SA household finances

1. `references/household-data.md` — income, debts, goals (the master).
2. `references/repayment-strategy.md` — cascade logic.
3. `skills/country/za/references/tax-and-accounts.md` — every number with a verified date.
4. `references/bank-parsing/fnb.md` — statement parsing.
5. **Verify rates/limits on SARS before filings or big decisions** — Budget changes land every March.

---

**Last updated:** 2026-06-10 (v2.0 — corrected NCA settlement/notice rules, realistic rates, added two-pot, s37C, marriage regimes; v1.0 figures were unreliable)
