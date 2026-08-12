---
name: Estate Planning
description: Estate planning and financial continuity. Triggered when household asks about wills, death planning, beneficiary designations, life insurance adequacy, or "what happens if I die?" Covers legal documents, insurance needs, digital estate, and partner continuity.
triggers:
  - "estate planning"
  - "will"
  - "death planning"
  - "beneficiary"
  - "life insurance"
  - "continuity plan"
  - "what if I die"
  - "guardianship"
  - "trust"
  - "inheritance"
  - "emergency contact"
voice: "Respectful, methodical, non-alarmist. This is unsexy but critical planning."
---

# Estate Planning — Legal Documents, Insurance, and Continuity

## Key Premise

Estate planning isn't morbid; it's love. The goal: if you're unable to work or manage finances, or if you die, the household continues smoothly and your wishes are honored. Without a plan, your partner and family face legal chaos and financial struggle at their worst moment.

## Step 1: Load Household Context

Read:
- `references/household-data.md` — dependents, current insurance, beneficiary info
- `references/estate-planning/estate-principles.md` — country-specific requirements
- CHANGELOG — any major life changes
- Current will/trust status (if exists)

Extract:
- Combined household income
- Dependents (children, disabled family)
- Debt obligations (mortgage, loans)
- Assets (home, vehicles, savings, investments)
- Current insurance coverage
- Marital/partnership status
- Country (determines legal requirements for wills, trusts, guardianship)

## Step 2: Load Estate Principles

Read: `skills/estate-planning/references/estate-principles.md`

This provides:
- Will essentials by country type
- Guardianship framework
- Beneficiary designation checklist
- Life insurance needs analysis formula
- Digital estate inventory template
- Document location checklist

## Step 3: Load Country Module

Read: `skills/country/[COUNTRY_CODE]/SKILL.md`

This provides country-specific:
- Will legal requirements (witnesses, notarization, etc.)
- Probate process (cost, timeline)
- Guardianship appointment process
- Inheritance tax laws (estate tax, death tax)
- Power of attorney rules
- Community property vs. common law

## Step 4: Run Estate Planning Analysis

Use this framework in this exact order:

### A. Life Insurance Adequacy

**Formula** (from estate-principles.md):
```
Target = (10-12x Annual Household Income)
         - Existing Coverage
         - Liquid Assets (savings)
```

**Example**:
```
Annual household income: $60,000
Multiple: 10 (conservative)
Existing coverage: $50,000
Liquid savings: $20,000

Target = (10 × $60,000) - $50,000 - $20,000
       = $600,000 - $50,000 - $20,000
       = $530,000 gap
```

**Output**: "You have a $530,000 life insurance gap. If you died today, your household would lack $530,000 to maintain standard of living, finish debt payoff, and fund children's education."

**Note**: This isn't the insurance company's limit; it's the actual household need.

### B. Will and Guardianship

**If no will exists**: This is urgent, especially if there are minor children.

**Minimum will should address**:
1. Who is the executor? (manages estate, settles debts, distributes assets)
2. Where do assets go? (spouse, children, trusts)
3. Who is guardian for minor children? (if both parents die)
4. Who manages children's inheritance until age 18/21/25?

**Not covered by will**: Accounts with beneficiary designations (life insurance, retirement accounts, some bank accounts). Those bypass probate and go directly to named beneficiary.

### C. Beneficiary Designation Audit

**Critical**: Beneficiary designations override the will. If you name someone in the account, they get it—regardless of what the will says.

**Accounts to check**:
- Life insurance policies (who's the primary/secondary beneficiary?)
- Retirement accounts (401k, IRA, TFSA, ISA)
- Bank savings accounts (some allow named beneficiary, some don't)
- Vehicles (some states allow beneficiary designation)

**Common mistake**: Divorce happens, beneficiary on life insurance is still the ex-spouse. Ex gets the insurance payout, not the new spouse.

**Action**: List all accounts and verify beneficiary designations match current wishes.

### D. Digital Estate

**What happens to online accounts?**

Banks, email, social media, investment accounts, cryptocurrency, photos, stored passwords—all at risk if the household is incapacitated or dies.

**Digital inventory** (from estate-principles.md):
- Email addresses and recovery methods
- Financial accounts (bank, investment, crypto)
- Social media (Facebook, Instagram, LinkedIn)
- Photo storage (Google Photos, iCloud, Dropbox)
- Password manager (or list of passwords in secure location)
- Business accounts (if applicable)
- Subscription services (recurring charges)

**Action**: Create a digital estate document. Store it somewhere secure (safe deposit box, password manager, trusted family member).

### E. Partner/Surviving Spouse Continuity Plan

**If you die, can your partner continue managing finances?**

This is often overlooked. Partner might be grieving, overwhelmed, and suddenly responsible for debt payments, taxes, insurance, investments.

**Continuity checklist**:
- Does partner know where debt statements are kept?
- Does partner understand the repayment cascade?
- Does partner have access to bank accounts?
- Does partner know what insurance policies exist?
- Does partner understand retirement accounts and their rules?
- Is there enough liquid cash (emergency fund) to survive 3-6 months without income?

**Action**: Have an explicit conversation with partner about finances. Walk them through the plan.

## Step 5: Address the Specific Question

Return to what the household asked:
- "Do we need a will?" → Yes, especially if dependent children
- "How much life insurance do we need?" → Use the formula above
- "What's a trust?" → Legal entity that holds assets; passes to beneficiaries without probate
- "Who should be the executor?" → Someone organized, trustworthy, and willing (talk to them first)
- "What if we can't decide who gets the kids?" → Have the hard conversation now, not in the will

## Important Principles

**1. Beneficiary designations override wills**
- If life insurance names ex-spouse, ex gets the money (even if will says otherwise)
- Update all designations after major life changes (marriage, divorce, children)

**2. Probate is slow and expensive**
- Assets outside the will (beneficiary accounts) skip probate (good)
- Assets in the will go through probate (slow, expensive)
- Trusts avoid probate (why some households use them)

**3. Guardianship is critical**
- If both parents die, court appoints guardian (might be someone you wouldn't choose)
- Name a guardian in your will so court knows your preference
- Talk to the proposed guardian first (ask if they're willing)

**4. This isn't tax advice**
- Some countries tax estates heavily (others don't)
- Some states have inheritance taxes
- Complex estates might benefit from trust strategies
- Consult a tax professional if estate is large or complex

**5. This is conversation, not final plan**
- These questions are hard and emotional
- The household should discuss together, then consult an attorney
- Attorney ensures the plan is legal in your jurisdiction

## Disclaimer

Include this disclaimer:

*I'm not a lawyer or estate planning professional. Estate planning laws vary significantly by country and state. This is a framework to start thinking about these issues. Before finalizing any plan, consult a qualified estate planning attorney in your jurisdiction. Nothing here is legal advice.*

---

## Response Template

```
# Estate Planning Review

## Your Situation
Household income: $[amount]
Dependents: [description]
Current life insurance: $[amount]
Liquid assets: $[amount]
Country: [Country]

## Life Insurance Analysis
Formula: (10-12x income) - existing - assets = gap
Calculation: ([multiple] × $[income]) - $[existing] - $[assets] = $[gap]

**Verdict**: You have a $[gap] life insurance gap.

## Critical Documents Checklist
- [ ] Will (naming executor, guardians, asset distribution)
- [ ] Beneficiary designations (life insurance, retirement accounts)
- [ ] Power of attorney (financial and medical)
- [ ] Advance healthcare directive (medical wishes)
- [ ] Digital estate inventory (accounts and access)

## Urgency
[Assess based on dependents, insurance gap, current age]
- If minor children: URGENT (address in next 30 days)
- If no will: Urgent (addresses in next 90 days)
- If beneficiary designations outdated: Address this month

## Next Steps
1. [Specific action 1]
2. [Specific action 2]
3. Consult an estate planning attorney in your jurisdiction

---
*I'm not a lawyer...*
```
