---
name: money-mentor-us
description: United States financial context module for Money Mentor. Covers USD currency, retirement accounts (401k, Roth IRA, HSA), FDCPA debt collection law, common US debt types, and Social Security basics.
status: active
---

# Money Mentor: United States Module

This module provides United States-specific financial guidance, including retirement account strategies, tax-advantaged savings, debt collection protections, and Social Security.

## Currency & Formatting

- **Currency:** US Dollar (USD)
- **Symbol:** $
- **Formatting:** $1,234.56 (dollar sign, comma separator, two decimal places)
- **Update triggers:** Automatically loaded when household profile specifies Country: US

## Bank Statement Parsing

Statement guides live in `references/bank-parsing/`. No US bank is pre-mapped yet — the system **learns each bank on first sighting**: parse the statement carefully, then save a new `<bank>.md` from `_TEMPLATE.md` (e.g. `chase.md`, `bofa.md`, `wells-fargo.md`, `capitalone.md`, `amex.md`) capturing that bank's description patterns, credit/debit convention, and category mapping. Note it in the CHANGELOG. See Finance Planner Step 2. Watch for US-specific quirks: ACH vs. wire, Zelle/Venmo/Cash App transfers, pending vs. posted, and check/e-check numbers.

## Tax-Advantaged Retirement Accounts (2026)

### 401(k) Plans (Employer-Sponsored)

**Contribution Limits (2026)**
- **Employee deferral limit:** $24,500/year
- **Age 50+ catch-up:** Additional $8,000/year (total: $32,500)
- **Ages 60-63 catch-up (SECURE 2.0):** Additional $11,250/year instead (total: $35,750)
- **Employer match limit:** Combined employee + employer contributions capped at $72,000

**Traditional vs. Roth 401(k)**
| Feature | Traditional | Roth |
|---|---|---|
| **Tax treatment of contributions** | Pre-tax (deductible) | After-tax (not deductible) |
| **Tax treatment of growth** | Tax-deferred | Tax-free |
| **Withdrawals in retirement** | Taxable as income | Tax-free |
| **Required Minimum Distributions (RMDs)** | Required at age 73 | Not required during lifetime |
| **Early withdrawal penalty** | 10% before 59.5 (with exceptions) | 10% before 59.5 + 5-year rule applies |
| **Income limits** | None | Income limits apply (phase-out for high earners) |

**Employer Match Strategy (CRITICAL)**
- **Always capture the full employer match** — it is free money with 100% immediate return
- If employer offers 3% match: contribute **at least 3%** of your salary
- If you cannot afford to do so: increase contribution as soon as possible
- Example: $50,000 salary, 3% match = $1,500/year free money; not capturing = permanent loss

**Vesting Schedule**
- **Immediate vesting:** Your contributions are always yours
- **Employer match vesting:** Employer-provided match vests on schedule (typically 3-6 years)
- If you leave before vesting: Forfeited match stays with employer plan
- **Strategy:** Know your vesting schedule; don't leave money on table

**Borrowing from 401(k)**
- Some plans allow loans (typically 50% of balance, max $50,000)
- You pay yourself back with interest (prime rate + 1%)
- **Caution:** If you leave the job, loan must be repaid within 60 days or treated as taxable distribution + 10% penalty
- **Better option:** Emergency fund or HELOC (if applicable) instead of 401(k) loan

### Roth IRA (Individual Retirement Account)

**Contribution Limits (2026)**
- **Annual limit:** $7,500/year
- **Age 50+ catch-up:** Additional $1,100/year (total: $8,600)
- **Income phase-outs (Single filer):**
  - $153,000–$168,000: Contribution ability phases out
  - Above $168,000: Cannot contribute directly to Roth

**Key Features**
- **Tax treatment:** After-tax contributions (not deductible); tax-free growth and withdrawals
- **No RMDs:** You never must withdraw (great for estate planning)
- **Early access:** Can withdraw contributions (not earnings) anytime tax/penalty-free
- **5-year rule:** Earnings cannot be withdrawn tax-free until 59.5 **and** account has been open 5+ years
- **Flexible:** Ideal if you expect higher tax brackets in retirement

**Backdoor Roth (High Earners)**
- Strategy for high-income earners over the income limit
- Contribute to Traditional IRA (non-deductible), then immediately convert to Roth
- Tax on conversion = pro-rata tax based on any existing pre-tax IRA balances
- **Caution:** "Pro-rata rule" means any pre-tax IRAs (SEP, SIMPLE, traditional) count; can create large unexpected tax bill

**Roth Ladder**
- Convert traditional IRA/401(k) to Roth in smaller tranches over several years
- Spreads tax bill across multiple years
- Allows early access to retirement funds (conversions taxed; withdrawals after 5-year rule tax-free)

### Traditional IRA (Individual Retirement Account)

**Contribution Limits (2026)**
- **Annual limit:** $7,500/year
- **Age 50+ catch-up:** Additional $1,100/year (total: $8,600)

**Tax Deductibility**
- **If no employer plan:** Fully deductible
- **If employer plan exists:** Phased out above certain income ($81,000–$91,000 single, 2026; $129,000–$149,000 married filing jointly)
- **Spouse with no plan:** Can deduct contributions (spousal IRA) even if other spouse has plan

**Withdrawals**
- **Before 59.5:** Subject to 10% early withdrawal penalty (plus income tax) with limited exceptions
- **RMDs:** Must begin withdrawing at age 73 (amount based on age and account balance)

### Health Savings Account (HSA)

**The Triple Tax Advantage**
1. **Contributions:** Tax-deductible (reduce your tax bill)
2. **Growth:** Tax-free investment growth
3. **Withdrawals:** Tax-free if used for qualified medical expenses

**Contribution Limits (2026)**
- **Self-only coverage:** $4,400/year
- **Family coverage:** $8,750/year
- **Age 55+ catch-up:** Additional $1,000/year

**Eligibility**
- Must be enrolled in high-deductible health plan (HDHP)
- Cannot be claimed as dependent on parents' tax return (for parent's insurance)
- Cannot have other health coverage (limited exceptions)

**Qualified Medical Expenses**
- Deductibles, copays, coinsurance
- Prescription drugs
- Dental, vision, hearing care (not covered by health insurance)
- Medical equipment (crutches, wheelchairs, blood pressure monitors)
- NOT covered: Cosmetic procedures, vitamins (unless prescribed), gym memberships

**Investment Option**
- HSA can be invested (stocks, bonds, mutual funds) not just kept as savings
- Growth is tax-free
- Can be used as supplemental retirement account (funds can stay invested)

---

## Debt: Types, Strategies, and Collections Law

### Common US Debt Types

**Student Loans**
- **Federal loans:** Subsidized (no interest while in school), unsubsidized (interest accrues)
  - Standard repayment: 10 years
  - Income-driven repayment: 20–25 years; forgiveness after (taxable as income)
  - Interest rate: Fixed ~5–8% (varies by program and year)
- **Private loans:** Variable interest rates, typically 4–12%, fewer forgiveness options
- **Payments:** Can be paused (deferment/forbearance); public service loan forgiveness (PSLF) available

**Credit Cards**
- **Interest rate:** 15–25% APR (average); varies by issuer and credit score
- **Minimum payment trap:** Paying only minimum keeps you in debt 5–10+ years
- **Strategy:** Pay full statement balance monthly; if carrying balance, prioritize by interest rate (avalanche)
- **Credit utilization:** Paying below 30% of limit improves credit score

**Auto Loans**
- **Typical terms:** 36–72 months (3–6 years)
- **Interest rate:** 4–10% depending on credit score and lender
- **Loan-to-value:** Lenders cap amount financed; larger down payment = lower rate
- **Early payoff:** Prepayment penalty rare; refinancing option if rate drops

**Personal Loans**
- **Unsecured:** Based on credit score and income
- **Terms:** 2–7 years
- **Interest rate:** 6–36% depending on credit score and lender
- **Use:** Debt consolidation, home improvement, emergency (avoid for lifestyle)

**Medical Debt**
- Increasingly common; ~43M Americans have medical debt in collections
- Often ignored on credit reports for 1–2 years (negotiation window)
- Settling for less than owed is common (especially if older debt)
- No interest charged (unlike credit cards) but can go to collections

**Mortgage**
- **Secured by home:** Lender can foreclose if not paid
- **Terms:** 15–30 years (30-year most common)
- **Interest rate:** 4–8% depending on market and credit score
- **Payments:** Principal + interest + taxes + insurance (PITI)
- **Early payoff:** Prepayment allowed; consider opportunity cost vs. investing at higher return

### Fair Debt Collection Practices Act (FDCPA)

**Your Rights Against Debt Collectors**
- **No harassment:** Cannot call repeatedly, use threats, call before 8am or after 9pm
- **Cease-and-desist:** Send written letter demanding collector stop contacting you; by law they must stop (except lawsuit/garnishment notice)
- **No collection after 6 years:** Debt "falls off" credit report; cannot pursue after statute of limitations (varies by state, typically 3–10 years)
- **Debt validation:** Right to request written proof collector owns the debt; if not provided within 30 days, debt cannot be collected

**How to Protect Yourself**
- Document all collector contacts (date, time, content)
- Send cease-and-desist letter via certified mail (evidence of receipt)
- Do not acknowledge debt verbally; request validation in writing
- File complaint with Consumer Financial Protection Bureau (CFPB) if violated

### Bankruptcy (Last Resort)

**Chapter 7 Bankruptcy**
- **Liquidation:** Non-exempt assets sold; unsecured debt (credit cards, personal loans) discharged
- **Timeline:** 3–6 months to discharge
- **Cost:** $300–500 filing fee + attorney fees ($1,500–3,000)
- **Eligibility:** Means test; must have income below state median to qualify
- **Credit impact:** Remains on credit for 7 years; can rebuild after

**Chapter 13 Bankruptcy**
- **Restructuring:** Court-approved repayment plan (3–5 years)
- **Pros:** Keep assets; stop foreclosure; lower payment obligations
- **Cons:** Must complete plan; takes 3–5 years; high legal costs
- **Best for:** Homeowners at risk of foreclosure; wage earners with regular income

**Before Bankruptcy:**
- Exhausted other options? (Negotiation, payment plan, hardship program)
- Consult bankruptcy attorney (many offer free initial consultations)
- Be aware: Student loans usually NOT discharged in bankruptcy

---

## Credit Score & Credit Reports

### FICO Score (300–850)

**Score Ranges & Interpretation**
| Score | Rating | Impact |
|---|---|---|
| 800–850 | Excellent | Best rates; easy approval |
| 740–799 | Very Good | Good rates; strong approval |
| 670–739 | Good | Fair rates; standard approval |
| 580–669 | Fair | Higher rates; conditional approval |
| Below 580 | Poor | Very high rates; difficult approval |

**What Impacts Your Score**
1. **Payment history (35%):** On-time payments are most important
2. **Credit utilization (30%):** Keep below 30% of available credit limits
3. **Length of credit history (15%):** Older accounts help
4. **Credit mix (10%):** Cards + auto loan + mortgage = better
5. **New credit inquiries (10%):** Hard pulls lower score temporarily

**Free Credit Reports**
- **Annual entitlement:** One free report per bureau per year at www.annualcreditreport.com
- **Three bureaux:** Equifax, Experian, TransUnion (check each separately)
- **Freeze:** Can freeze credit to prevent unauthorized accounts; free to place/lift

---

## Retirement & Social Security

### Social Security Basics

**Eligibility & Benefit Amount**
- **Qualifying:** 40 "credits" (roughly 10 years of work) required to claim benefits
- **Full retirement age:** 66–67 depending on birth year
- **Earliest claim:** Age 62 (reduced benefit, ~70% of full amount)
- **Delayed claim:** Wait until 70 (increased benefit, ~124% of full amount)
- **Benefit amount:** Based on 35 highest-earning years; adjusted for inflation

**Spousal & Survivor Benefits**
- **Spousal benefit:** Non-working spouse can claim up to 50% of worker's benefit at full retirement age
- **Survivor benefit:** Spouse and children can collect if worker passes away

**Taxation of Benefits**
- If combined income (50% of benefits + other income) exceeds $25,000 (single), up to 50% of benefits taxable
- If exceeds $34,000 (single), up to 85% of benefits taxable

**Claiming Strategy**
- **Early claim (62):** Receive payments immediately but permanently reduced
- **Full retirement age:** Receive full benefit
- **Delayed claim (70):** Larger monthly payments; breakeven around age 80–82
- **Strategy:** If healthy/long-lived family history, delaying increases lifetime benefits

### Retirement Planning Framework

**The 4% Rule**
- Safe withdrawal rate from retirement portfolio: ~4% of balance first year, adjusted for inflation
- Example: $1M portfolio = $40,000 first year withdrawals
- Allows 30-year+ retirement with low probability of depleting assets

**Required Minimum Distributions (RMDs)**
- Traditional IRA, 401(k), etc.: Must begin withdrawing at age 73
- Amount calculated by IRS based on age and account balance
- Penalty for insufficient withdrawal: 10% (plus income tax) on shortfall
- **Roth IRA:** No RMDs during your lifetime (major advantage)

---

## Insurance & Protection

### Health Insurance

**Types**
- **Employer-sponsored:** Most Americans; coverage + contribution shared with employer
- **ACA Marketplace:** For self-employed, unemployed, or employer coverage unavailable
- **Medicare:** Age 65+; covered by Social Security taxes during working years
- **Medicaid:** Income-based; varies by state

**Key Terms**
- **Deductible:** Amount you pay before insurance begins covering costs
- **Copay/Coinsurance:** Your share of each medical service
- **Out-of-pocket maximum:** Most you'll pay in a year; insurance covers 100% after
- **Network:** Doctors/hospitals covered; out-of-network costs more

### Auto Insurance (Required by Law)

**Minimum coverage (liability):**
- $25,000 bodily injury per person
- $50,000 bodily injury per accident
- $25,000 property damage
- Many states require more; check your state

**Optional coverage:**
- **Collision:** Covers accidents (your car)
- **Comprehensive:** Covers theft, weather, vandalism
- **Uninsured motorist:** Covers hits from uninsured drivers
- **Gap insurance:** Covers difference between car value and loan owed (if totaled)

### Homeowners/Renters Insurance

- **Homeowners:** Covers structure + contents + liability; typically R$800–2,000/year
- **Renters:** Covers your belongings + liability; typically $150–300/year
- **Liability coverage:** Protects if someone injured at your home (lawsuit)

### Life Insurance

**Term Life (Recommended)**
- Covers 10–30 year term; cheapest option
- $500k–$2M typical; $20–100/month depending on age/health
- **Best use:** Family with dependents (income replacement)

**Whole Life (Permanent)**
- Covers entire lifetime; includes cash surrender value
- **Cost:** 5–10x more expensive than term
- **Best use:** Wealthy estates needing permanent coverage for tax purposes

**Rule of thumb:** 10x annual income in coverage; decreases as you age and assets grow

### Disability Insurance

- **Short-term:** 3–6 months coverage; employer often provides
- **Long-term:** Age 65+ or end of disability; replaces 50–70% of income
- **Importance:** Statistically more likely to be disabled than to die (age 35–65)
- **Cost:** Employer-sponsored usually subsidized (cheap); individual policies $50–200+/month

---

## Common Mistakes to Avoid

1. **Not capturing 401(k) match:** Free money; always contribute at least to match
2. **Early 401(k) withdrawal:** 10% penalty + income tax; only in true emergency
3. **Carrying credit card balance:** 18–24% interest kills wealth-building
4. **Ignoring medical debt:** Negotiate settlement; often willing to accept 30–50% payoff
5. **Claiming Social Security at 62:** Reduces benefit by ~30%; only if health/cash crisis
6. **Backdoor Roth mistake:** Failing to account for pro-rata rule = large tax surprise
7. **Student loan neglect:** Income-driven repayment options available; explore forgiveness
8. **No emergency fund:** Leads to high-interest debt when crisis hits
9. **Lifestyle inflation after debt payoff:** Freed-up payment goes to new debt instead of investment

---

## Key Resources

- **CFPB Consumer Complaint Database:** Report debt collector violations
- **SSA.gov:** Estimate Social Security benefits, manage account online
- **Annualcreditreport.com:** Free annual credit report (all three bureaux)
- **IRA.gov:** IRS retirement account guidance
- **HealthCare.gov:** ACA marketplace insurance options

---

**Last updated:** 2026-08-12 (JP) - figures verified against IRS Rev. Proc. 2025-32, Notice 2025-67 and Rev. Proc. 2025-19
**Version:** 1.0
