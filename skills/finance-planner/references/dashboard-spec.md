# Dashboard Specification

Monthly progress dashboard (PowerPoint presentation). Single main slide with clean visual hierarchy.

## Design Overview

**File**: `dashboards/progress_dashboard.pptx`
**Slide size**: Standard 16:9
**Main slide layout**: Two-column

| Left Column (40%) | Right Column (60%) |
|------------------|-------------------|
| Debt Progress    | Debt Details       |
| Interest Burn    | Milestones         |
| Debts Cleared    | Insurance Summary  |

---

## Color Palette

```
Navy (Primary):       #1B2A4A   (backgrounds, headings)
Gold (Accent):        #D4A843   (progress bars, highlights)
Green (Success):      #4CAF50   (cleared debts, positive metrics)
Red (Alert):          #EF5350   (high-interest debt, risks)
Grey (Secondary):     #B0BEC5   (secondary text, lines)
White (Base):         #FFFFFF   (content areas)
```

---

## Left Column — Progress Visualization

### 1. Debt Freedom Progress Bar

**Title**: "Debt Freedom Progress"
**Layout**: Horizontal progress bar + percentage

**Data source**: `(Total Original Debt - Current Total Debt) / Total Original Debt × 100`

**Visual**:
```
Debt Freedom Progress
████████░░░░░░░░░░ 42%
$156,500 eliminated of $368,000

Progress Rate: 4 months ahead of plan
```

**Color scheme**:
- Filled portion: Gold (#D4A843)
- Empty portion: Light grey (#E0E0E0)
- Percentage text: Navy (#1B2A4A), bold 24pt

**Update frequency**: Monthly (on the 1st of each month)

### 2. Interest Burn Rate

**Title**: "Monthly Interest Burn"
**Layout**: Current amount + benchmark + trend

**Data source**: Sum of (Balance × Annual Rate / 12) for all active debts

**Visual**:
```
Monthly Interest Burn
Current:   $623/month
Baseline:  $650/month
Trend:     ↓ -4% (improving)

12-month projection: $450/month
```

**Color scheme**:
- If current < baseline: Green (#4CAF50) ✓
- If current > baseline: Red (#EF5350) ⚠
- Trend arrow: Green if improving, red if worsening

**Benchmark source**: `references/household-data.md` → Baseline Interest field (use Feb 2026 first run)

### 3. Debts Cleared Count

**Title**: "Milestone"
**Layout**: Count + list of cleared debts

**Visual**:
```
Debts Cleared
2 out of 5

✓ Creditor A (cleared Jan 2026)
✓ Creditor B (cleared Feb 2026)
⏳ Current target: Creditor C
```

**Color scheme**:
- Cleared: Green checkmark (#4CAF50)
- Active: Gold progress indicator (#D4A843)
- Font: Navy headings, grey text

---

## Right Column — Strategic Details

### 1. Current Target Debt

**Title**: "Current Target"
**Layout**: Name + balance + progress + clearance date

**Data source**: From `references/repayment-strategy.md` and monthly cascade calculation

**Visual**:
```
Current Target
Creditor Name
$8,170 remaining
150/month minimum
500/month extra payment

Target clearance: Aug 2027 (18 months)
Current pace: ON TRACK
```

**Progress sub-bar** (mini horizontal bar showing target progress):
```
████████░░░░░░░░░░ 46% of balance cleared
```

**Color**:
- Heading: Navy (#1B2A4A)
- Balance: Red (#EF5350) or Gold (#D4A843) depending on rate
- Clearance date: Green if on track, amber if at risk

### 2. Next 3 Milestones

**Title**: "Upcoming Milestones"
**Layout**: Timeline list

**Data source**: Waterfall projection from cascade calculation

**Visual**:
```
Upcoming Milestones

1️⃣  Creditor C cleared
    Aug 2027 (18 months away)

2️⃣  Creditor D cleared
    Jan 2028 (24 months away)

3️⃣  All consumer debt cleared
    Mar 2030 (48 months away)
    💰 Start wealth building
```

**Color scheme**:
- Milestone number: Gold circle (#D4A843)
- Dates: Navy text (#1B2A4A), secondary font size
- Final milestone: Green background (#4CAF50)

### 3. Insurance Coverage Summary

**Title**: "Insurance Status"
**Layout**: Checklist

**Data source**: `references/household-data.md` → Insurance section

**Visual**:
```
Insurance Coverage
✓ Life insurance (adequacy: 87%)
✓ Disability cover (income protection)
✓ Home & vehicle insured
⚠ Umbrella liability (recommended)
```

**Color scheme**:
- ✓ Covered: Green (#4CAF50)
- ⚠ Recommended: Amber (#FFB74D)
- ✗ Missing: Red (#EF5350)
- Font: 10pt, secondary grey (#B0BEC5)

---

## Slide Structure (PowerPoint XML/Visual)

```
┌─────────────────────────────────────────────────────┐
│                                                       │
│  HOUSEHOLD FINANCIAL PROGRESS — March 2026           │
│                                                       │
├──────────────────────────┬──────────────────────────┤
│                          │                          │
│  LEFT COLUMN (40%)       │  RIGHT COLUMN (60%)      │
│                          │                          │
│  Debt Freedom Progress   │  Current Target          │
│  ████████░░░░░░░░░░ 42%  │  [Details]              │
│                          │                          │
│  Monthly Interest Burn   │  Upcoming Milestones     │
│  $623 (↓ -4%)           │  • Clearance 1           │
│                          │  • Clearance 2           │
│  Debts Cleared           │  • Clearance 3           │
│  2 of 5 ✓               │                          │
│                          │  Insurance Status        │
│                          │  ✓ ✓ ✓ ⚠               │
│                          │                          │
└──────────────────────────┴──────────────────────────┘
```

---

## Typography Specifications

| Element | Font | Size | Weight | Color |
|---------|------|------|--------|-------|
| Page Title | Arial | 28 | Bold | #1B2A4A |
| Section Headers | Arial | 16 | Bold | #1B2A4A |
| Metric Labels | Arial | 12 | Normal | #B0BEC5 |
| Metric Values | Arial | 18 | Bold | #1B2A4A or #EF5350 |
| Body text | Arial | 11 | Normal | #424242 |
| Footnotes | Arial | 9 | Italic | #B0BEC5 |

---

## Data Update Sources

Each month, pull these:

1. **Total debt balance**: Sum of all creditor balances from statements/creditor files
2. **Interest burn**: Calculate from Step 6 (Finance Planner)
3. **Target debt name & balance**: From repayment-strategy.md current phase
4. **Clearance timeline**: From cascade waterfall calculation
5. **Debts cleared**: Count from archive summaries (search for "cleared" status)
6. **Insurance status**: From household-data.md Insurance section

---

## Milestone Slide Rule

**When a debt is fully cleared**, create an additional slide immediately following the main slide:

### Milestone Achieved Slide

**Layout**: Full-screen celebration

**Visual**:
```
┌──────────────────────────────────────────────────────┐
│                                                        │
│                    🎉 MILESTONE! 🎉                   │
│                                                        │
│              [Creditor Name] Cleared                  │
│                   [Date Cleared]                      │
│                                                        │
│         Total Debt Eliminated: $[amount]              │
│         Monthly Cash Flow Freed: $[min payment]       │
│                                                        │
│             Next target: [Next Creditor]              │
│             Estimated clearance: [Month Year]         │
│                                                        │
└──────────────────────────────────────────────────────┘
```

**Styling**:
- Background: Gradient from navy (#1B2A4A) to gold (#D4A843)
- Text: Large, white, centered
- Emoji: Celebration and progress indicators
- Keep on slide deck for 1 month, then archive

---

## Update Process

**Monthly steps** (after Finance Planner runs):

1. Open `dashboards/progress_dashboard.pptx`
2. Update title: Replace month/year with current month
3. Left Column:
   - Recalculate progress %: (Original - Current) / Original
   - Update progress bar fill (Excel/Sheets formula or manual graphic update)
   - Update Interest Burn $: run calculation
   - Update Debts Cleared count
4. Right Column:
   - Update target debt name, balance, clearance date
   - Update Milestones list (recalculate from cascade)
   - Update Insurance Status (review household-data.md)
5. If any debt cleared: Add Milestone slide
6. Save and date the file: `progress_dashboard_2026_03.pptx`

---

## File Naming Convention

Main slide: `progress_dashboard.pptx` (active/current)
Archive: `progress_dashboard_YYYY_MM.pptx` (monthly backups)

Example: `progress_dashboard_2026_03.pptx` (March 2026)

---

## Accessibility Notes

- All progress bars include % text (not just visual)
- Color choices pass WCAG AA contrast requirements
- Font sizes >= 11pt for readability on projectors
- No information conveyed by color alone (use checkmarks, text, icons)

