# FNB Bank Statement Parsing Guide

## Overview

FNB (First National Bank) statements are typically **3-page PDF documents**, one per calendar month. This guide describes patterns used to identify and categorize transactions.

---

## Statement Layout & Structure

### Header Information
- Bank name: "First National Bank"
- Account holder name
- Account number (masked, e.g., `****1234`)
- Statement period: 1st to last day of calendar month
- Opening balance (previous month's closing balance)
- Closing balance (end of current month)

### Main Transaction Table
Columns (left to right):
1. **Date:** Transaction date (DD/MM or DD Mmm)
2. **Description:** Text describing the transaction (see patterns below)
3. **Amount:** Numerical value (sometimes with "Cr" suffix for credit)
4. **Balance:** Running balance after transaction

### Footer
- Statement summary: Opening balance, deposits, withdrawals, closing balance
- Bank contact details and fraud hotline
- Page number and statement reference

---

## Transaction Type Patterns

### Salary / Income Deposits
**Pattern:** Large credit (income) appearing on or near salary date (typically 25th–28th of month)

**Example descriptions:**
- `Salary Deposit [Employer Name]`
- `EFT FROM [Employer Name]`
- `Deposit [Company Code]`
- `Credit [Department] – [Employee ID]`

**Identifying markers:**
- Amount is large (typically 30–50%+ of monthly expenses)
- Occurs on predictable date monthly
- Shows as credit (positive value) on statement
- May have "Cr" suffix on amount column

**Parsing tip:** First occurrence of large regular credit = salary. Verify against expected salary date.

---

### Debit Orders (Standing Orders)

**Pattern:** Recurring automatic debits for subscriptions, insurance, loan payments, utilities

**Example descriptions:**
- `Magtape Debit [Provider Name]`
- `DebiCheck [Provider Name]`
- `Standing Order [Recipient Description]`
- `Electricity Debit [Provider Reference]`
- `Insurance Debit [Insurer Name]`

**Common providers:**
- Electricity: `Eskom Debit`, `City Power Debit`, `Municipal Debit`
- Insurance: `Discovery Debit`, `Hollard Debit`, `Old Mutual Debit`
- Loan payments: `WesBank Debit`, `Truworths Debit`, `Standard Bank Debit`
- Internet/Telco: `Vodacom Debit`, `MTN Debit`, `Telkom Debit`

**Parsing tip:** Debit orders are regular and predictable; use occurrence date to flag budget items.

---

### POS Purchases (Point of Sale)

**Pattern:** Physical card swipes at retail stores, petrol stations, restaurants

**Example descriptions:**
- `POS Purchase [Merchant Name]`
- `Card Purchase [Store Code] [Store Name]`
- `Purchase [Retailer] – [Location]`

**Common merchants:**
- Supermarkets: `Pick n Pay`, `Shoprite`, `Checkers`, `Woolworths`
- Fuel: `Shell`, `BP`, `Engen`, `Caltex`
- Restaurants: `Restaurant Name`, `Cafe`, `Fast Food Chain`
- Retail: `Truworths`, `Mr Price`, `Edgars`, `Takealot`

**Amount:** Variable; can be single items (R50) or bulk shopping (R3,000+)

**Parsing tip:** Look for merchant names in description; group by category for budget tracking.

---

### Internet Banking Payments (Manual Transfers)

**Pattern:** User-initiated transfers to other accounts (not debit orders)

**Example descriptions:**
- `Internet Pmt To [Recipient Name]`
- `Internet Transfer [Account Holder Name]`
- `Transfer To [Recipient Bank] [Account Reference]`
- `Internet Payment [Description]`

**Common uses:**
- Loan payments (manual payment instead of debit order)
- Transfers to savings account
- Payments to service providers (not debit order)
- Peer-to-peer transfers

**Parsing tip:** Manual transfers require user initiation; date and amount vary. Can indicate irregular or one-off payments.

---

### Internal Transfers (Between Own Accounts)

**Pattern:** Transfers between your own FNB accounts (e.g., cheque to savings)

**Example descriptions:**
- `Internal Debit Order [Desc]`
- `Transfer To [Own Account Type]`
- `Internal Transfer [Account Designation]`

**Identifying markers:**
- Both debit and corresponding credit appear (one on each account)
- Account numbers at same bank (FNB)
- Often used for savings goals or cash management

**Parsing tip:** Internal transfers are not expense categories; they're account movements. Exclude from spending summaries.

---

### Bank Fees & Service Charges

**Pattern:** Monthly or transaction-based fees charged by the bank

**Example descriptions:**
- `#Monthly Account Fee`
- `#Monthly Credit Fee` (fee for overdraft interest)
- `#Card Fee`
- `#Cheque Deposit Fee`
- `#Debit Order Rejection Fee`
- `#Overdraft Interest Charge`

**Amount:** Typically R5–80 depending on account tier and transaction volume

**Parsing tip:** Fees are fixed monthly costs. Review account type to see if downgrading saves money.

---

### Prepaid Purchases

**Pattern:** Purchase of prepaid services (electricity, airtime, data)

**Example descriptions:**
- `Electricity Prepaid [Meter Number]`
- `Eskom Prepaid Electricity`
- `Airtime Purchase [Network Operator]`
- `Data Purchase [Provider]`
- `Water Prepaid [Reference]`

**Identifying markers:**
- Reference number or account number in description (meter, phone)
- Amount varies (R100–2,000+ for electricity)
- Shows immediately as debit

**Parsing tip:** Prepaid amounts are expense (not balance carried forward). Track separately from other utilities.

---

### Returned/Reversed Transactions

**Pattern:** Previous transaction cancelled or refunded

**Example descriptions:**
- `REVERSAL: [Original Transaction Description]`
- `CANCELLED: [Transaction Description]`
- `REFUND: [Original Merchant]`

**Identifying markers:**
- Often appears days after original transaction
- Same amount as original (reversed/credited back)
- Description includes "REVERSAL", "CANCELLED", or "REFUND"

**Parsing tip:** When reconciling, match reversals to original transactions (net them out, don't double-count).

---

### ATM Withdrawals

**Pattern:** Cash withdrawal from ATM (FNB or other bank)

**Example descriptions:**
- `ATM Withdrawal [Location/Branch Code]`
- `Cash Withdrawal [ATM Location]`
- `ATM [Branch Name]`

**Identifying markers:**
- Fixed denominations (often R100, R500 multiples)
- Location or branch code in description
- Debit to account (cash leaves your account)

**Parsing tip:** ATM withdrawals often represent cash spending (groceries, transport, tips). Track separately if possible.

---

### Cheque Deposits

**Pattern:** Deposited cheques (less common with digital banking)

**Example descriptions:**
- `Cheque Deposit [Cheque Number]`
- `Cheque Credit [Reference]`

**Identifying markers:**
- Cheque number often included
- Shows as credit (deposit)
- May take 2–3 business days to clear

**Parsing tip:** Note clearing delay; cheques may not appear immediately on statement.

---

### Foreign Exchange Transactions

**Pattern:** Currency conversions for international payments or transfers

**Example descriptions:**
- `FX Purchase [Currency] [Reference]`
- `International Transfer [Country] [Recipient]`
- `Wire Transfer [Recipient Bank] [Account]`

**Identifying markers:**
- Currency code (USD, GBP, EUR, etc.) in description
- Higher fees than domestic transfers
- Amount shown in ZAR; may include FX margin

**Parsing tip:** Note FX rate and margin (typically 2–3%); budget for international payments separately.

---

## Reading the Statement Correctly

### Credit Indicator
- **"Cr" suffix (or parentheses):** Positive transaction (money coming in)
  - Example: `R5,000 Cr` = deposit/credit to account
- **No suffix:** Debit (money going out)
  - Example: `R500` = debit/withdrawal from account
- **Negative balance:** Account is in overdraft (if permitted by bank)

### Running Balance
- **Balance column:** Always shows account balance **after** that transaction
- **Example:**
  - Opening balance: R10,000
  - Debit R2,000 → Balance shown: R8,000
  - Credit R1,000 → Balance shown: R9,000

---

## Common Categorization Framework

Use these categories when reconciling statements against budget:

| Category | Transaction Types | Example |
|---|---|---|
| **Income** | Salary, bonuses, interest, refunds | Salary Deposit, Interest Credit |
| **Utilities** | Electricity, water, gas, internet | Eskom Debit, Telkom Debit |
| **Insurance** | Life, vehicle, home, medical aid | Discovery Debit, Hollard Debit |
| **Loan Repayments** | Vehicle, personal loans | WesBank Debit, Standard Bank Debit |
| **Store Credit** | Revolving store accounts | Truworths Debit, Mr Price Debit |
| **Groceries** | Supermarket, fruit/veg markets | Pick n Pay, Shoprite, Checkers |
| **Fuel** | Petrol, diesel | Shell, BP, Engen |
| **Dining & Entertainment** | Restaurants, bars, cinemas | Restaurant POS, Fast Food POS |
| **Transport** | Taxis, Uber, parking, tolls | Uber POS, Toll Debit |
| **Healthcare** | Pharmacy, doctor, dentist | Pharmacy POS, Medical Deposit |
| **Personal Care** | Salon, gym, haircut | Salon POS, Gym Debit |
| **Retail Shopping** | Clothing, electronics | Truworths POS, Takealot POS |
| **Bank Fees** | Monthly fees, transaction charges | Monthly Account Fee |
| **Cash Withdrawals** | ATM withdrawals (untracked spend) | ATM Withdrawal |

---

## Tips for Accurate Parsing

1. **Verify dates:** Statement date range is always 1st to last day of calendar month
2. **Check for duplicates:** Some merchants appear on same date with same amount → possible duplicate, verify once
3. **Note unusual dates:** Salary on unusual date (not 25th) → flag as exception
4. **Watch for timing:** Debit orders processed mid-to-late month; some may reflect prior month's accrual
5. **Look for "Cr":** Always check for credit indicator; easy to misread debit vs. credit
6. **Cross-reference amounts:** Large one-off purchases should be recognized; unusual amounts → verify accuracy
7. **Identify patterns:** First occurrence of new debit order (e.g., new insurance) → add to budget
8. **Check for fraud:** Unknown merchants or unusual dates → flag for verification
9. **Reconcile totals:** Sum of debits + opening balance should equal closing balance (accounting check)
10. **Keep context:** Multiple small debits on same date often indicate multiple transactions same merchant (not fraud)

---

## Example Statement Snippet

```
Date       Description                           Amount      Balance
01/03      Opening Balance                                   10,500.00
25/03      Salary Deposit XYZ Corp            47,500.00 Cr  58,000.00
26/03      Eskom Debit                         1,850.00      56,150.00
26/03      Discovery Debit (Insurance)           620.00      55,530.00
27/03      Truworths Debit (Store CC)           800.00      54,730.00
28/03      Pick n Pay POS                       450.50       54,279.50
28/03      Shell Petrol POS                     550.00       53,729.50
29/03      Internet Pmt To Savings Account    5,000.00 Cr   58,729.50
30/03      #Monthly Account Fee                  35.00       58,694.50
31/03      Closing Balance                                   58,694.50
```

### Parsing this example:
- **Income:** R47,500 (salary)
- **Utilities:** R1,850 (Eskom)
- **Insurance:** R620 (Discovery)
- **Debt (store):** R800 (Truworths)
- **Groceries:** R450.50 (Pick n Pay)
- **Fuel:** R550 (Shell)
- **Savings transfer:** R5,000 (internal movement, not expense)
- **Fees:** R35 (bank fee)

---

**Last updated:** 2026-03-04
**Version:** 1.0
