# Money Mentor

A personal finance management plugin for Claude's Cowork mode. Track your income, eliminate debt, and build wealth — with AI-powered analysis, monthly processing, and progress dashboards.

## What It Does

Money Mentor turns Claude into your household's financial accountability partner. It manages the full lifecycle from "drowning in debt" to "building wealth":

**Debt Elimination** — Uses a hybrid snowball/avalanche strategy to attack your debts in the optimal order. Tracks every payment, calculates freed minimums cascading forward, and shows your interest burn rate dropping month over month.

**Monthly Processing** — Drop your bank statements into the folder, say "process [month] finances", and get a complete reconciliation: budget vs actuals, updated debt balances, recalculated snowball, goal contributions, payment plan split by pay date, and a progress dashboard. It **learns as it goes** — the format of each new bank on first sighting, and which merchants belong in which category — and keeps rolling category averages so your budget drifts toward how you actually spend.

**Financial Analysis** — Say "money mentor" or "check our strategy" for an on-demand analysis grounded in your actual numbers. Draws on principles from Ramsey, Sethi, Housel, Bach, Collins, and more.

**Goal Planning** — Saving toward something specific — a move, a car, a holiday, a house deposit? Goal Planner turns each goal into a monthly sinking-fund contribution, tracks progress, and sequences it sensibly against debt and your emergency fund. For people whose main job isn't debt, this is the front seat, not an afterthought.

**Wealth Building** — Once debt is cleared, transitions to emergency fund building, tax-advantaged account maximization, and long-term investing guidance.

**Estate Planning** — Life insurance adequacy checks, will essentials, beneficiary audits, and partner continuity planning.

## Supported Countries

Each country module provides the right currency formatting, tax-advantaged accounts, relevant legislation, and local financial context:

- **South Africa** — ZAR, TFSA, Retirement Annuity, NCA rules, FNB statement parsing
- **United States** — USD, 401(k), Roth IRA, HSA, FDCPA, federal tax brackets

Only the countries I can actually keep current ship here. UK and Australia/NZ modules exist but are held back until their tax data is verified rather than published stale - wrong tax figures are worse than no tax figures.

## Getting Started

You can use Money Mentor two ways:

**A. As a Cowork add-in**
1. Add the plugin in Cowork (point it at this repo)
2. Select a folder for your finances

**B. By cloning the repo**
1. Clone it:
   ```
   git clone https://github.com/JPPieterse/money-mentor.git
   ```
2. Make the skills and `/setup` command available to Claude Code (place or symlink the plugin where your Claude picks up plugins), and pick a folder for your finances

**Then, either way:**
3. Run `/setup` to walk through the guided onboarding — it asks about your whole picture, then tells you the best path (debt, goals, wealth, or estate), not a one-size-fits-all script
4. Setup creates your financial profile plus only the pieces you need (debt strategy if you have debt, a goal plan if you have goals, a spending baseline that learns your categories)
5. Start processing: drop a bank statement and say "process [month] finances" — it learns each new bank and your spending as it goes

## Privacy

All your personal data stays in local files on your computer. The plugin's skills read from your `references/household-data.md` on demand — nothing is hardcoded, nothing is stored remotely. The plugin ships with zero personal data (templates and examples only).

**Model-training note.** On Claude **Free, Pro, and Max** plans, your chats and coding sessions are used to improve Anthropic's models **unless you opt out**. Since you'll be handling financial documents here, consider turning that off before you start: **Settings → Privacy → turn off using your chats/coding sessions to improve Claude** (changeable any time). This does **not** apply to Team, Enterprise, or API accounts, which aren't used for training. *(Reflects Anthropic's consumer terms as of Aug 2025 — verify current settings, as policies change.)*

## What's Included

### Skills
- **Money Mentor** — On-demand financial analysis and strategy review
- **Finance Planner** — Monthly statement processing, category learning, and dashboard generation
- **Goal Planner** — Sinking funds for named goals (a move, a car, a holiday, a deposit)
- **Wealth Builder** — Post-debt investment and savings strategy
- **Estate Planning** — Wills, insurance, beneficiaries, continuity planning
- **Country Modules** — South Africa and United States financial context

### Commands
- `/setup` — Full guided onboarding (creates all files and folder structure)

### Templates
- `household-data.md` — Blank household financial profile
- `repayment-strategy.md` — Debt elimination strategy template
- `goal-plan.md` — Sinking-fund plan for named goals
- `spending-baseline.md` — Learned merchant→category map and rolling category averages
- `CLAUDE.md` — Project context for your finance folder
- `FOLDER_INSTRUCTIONS.md` — Cowork folder configuration
- `FinPlan_template.xlsx` — Budget and debt tracking spreadsheet

## Tone

Direct, warm, no-nonsense. Money Mentor is your accountability partner — it will celebrate your wins and push back when you're leaving money on the table. It anchors every recommendation to your actual numbers, not generic advice.

## Disclaimer

Money Mentor is not a licensed financial advisor. It applies personal finance principles to your household data to provide analysis and recommendations. For binding financial decisions (insurance changes, investment mandates, legal settlements), confirm with a qualified financial planner in your country.

## License

MIT
