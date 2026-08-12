# Money Mentor

A personal finance management plugin for Claude's Cowork mode. Track your income, eliminate debt, and build wealth — with AI-powered analysis, monthly processing, and progress dashboards.

## What It Does

Money Mentor turns Claude into your household's financial accountability partner. It manages the full lifecycle from "drowning in debt" to "building wealth":

**Debt Elimination** — Uses a hybrid snowball/avalanche strategy to attack your debts in the optimal order. Tracks every payment, calculates freed minimums cascading forward, and shows your interest burn rate dropping month over month.

**Monthly Processing** — Drop your bank statements into the folder, say "process [month] finances", and get a complete reconciliation: budget vs actuals, updated debt balances, recalculated snowball, payment plan split by pay date, and a progress dashboard.

**Financial Analysis** — Say "money mentor" or "check our strategy" for an on-demand analysis grounded in your actual numbers. Draws on principles from Ramsey, Sethi, Housel, Bach, Collins, and more.

**Wealth Building** — Once debt is cleared, transitions to emergency fund building, tax-advantaged account maximization, and long-term investing guidance.

**Estate Planning** — Life insurance adequacy checks, will essentials, beneficiary audits, and partner continuity planning.

## Supported Countries

Each country module provides the right currency formatting, tax-advantaged accounts, relevant legislation, and local financial context:

- **South Africa** — ZAR, TFSA, Retirement Annuity, NCA rules, FNB statement parsing
- **United States** — USD, 401(k), Roth IRA, HSA, FDCPA, federal tax brackets

Only the countries I can actually keep current ship here. UK and Australia/NZ modules exist but are held back until their tax data is verified rather than published stale - wrong tax figures are worse than no tax figures.

## Getting Started

1. Install the plugin in Cowork
2. Select a folder for your finances
3. Run `/setup` to walk through the guided onboarding
4. The setup creates your complete financial profile, debt strategy, folder structure, and budget spreadsheet
5. Start processing: drop a bank statement and say "process [month] finances"

## Privacy

All your personal data stays in local files on your computer. The plugin's skills read from your `references/household-data.md` on demand — nothing is hardcoded, nothing is stored remotely. The plugin ships with zero personal data (templates and examples only).

## What's Included

### Skills
- **Money Mentor** — On-demand financial analysis and strategy review
- **Finance Planner** — Monthly statement processing and dashboard generation
- **Wealth Builder** — Post-debt investment and savings strategy
- **Estate Planning** — Wills, insurance, beneficiaries, continuity planning
- **Country Modules** — South Africa and United States financial context

### Commands
- `/setup` — Full guided onboarding (creates all files and folder structure)

### Templates
- `household-data.md` — Blank household financial profile
- `repayment-strategy.md` — Debt elimination strategy template
- `CLAUDE.md` — Project context for your finance folder
- `FOLDER_INSTRUCTIONS.md` — Cowork folder configuration
- `FinPlan_template.xlsx` — Budget and debt tracking spreadsheet

## Tone

Direct, warm, no-nonsense. Money Mentor is your accountability partner — it will celebrate your wins and push back when you're leaving money on the table. It anchors every recommendation to your actual numbers, not generic advice.

## Disclaimer

Money Mentor is not a licensed financial advisor. It applies personal finance principles to your household data to provide analysis and recommendations. For binding financial decisions (insurance changes, investment mandates, legal settlements), confirm with a qualified financial planner in your country.

## License

MIT
