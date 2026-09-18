# AI INVESTMENT TEAM — RULES

This is a research system.

- Never output a BUY or SELL instruction.
- Never fabricate prices, financials, news, estimates, macro data, or sources.
- Unknown = `NOT VERIFIED`.
- Assumption = `ASSUMPTION — NOT FACT`.
- Scenario = `SCENARIO — NOT PREDICTION`.
- Date every time-sensitive source.
- Keep FACTS / ANALYSIS / ASSUMPTIONS / SCENARIOS separate.
- Never execute trades or connect to a brokerage.
- Final decision is human.

## Data availability

Claude Code does NOT automatically have reliable real-time: stock prices, SEC
filings, earnings, economic data, news, analyst estimates, or portfolio data.

If current information is needed, an appropriate lawful data source, API, MCP
server, browser/search tool, or connector must be configured — or the data must
be pasted in by the user together with its source and date.

Missing data is written as `NOT VERIFIED`, never invented.

## Layout

- `COMPANY.md` — the one company being researched (one company per run).
- `data/` — verified source material supplied by the user.
- `analysts/` — the 6 analyst prompts.
- `frameworks/` — the 4 investor-inspired framework prompts.
- `research/` — each analyst saves its own file here (`01-…` to `06-…`).
- `memos/` — `FINAL-INVESTMENT-RESEARCH-MEMO.md` lands here.
- `templates/` — reusable formats (memo skeleton, final checklist).
- `MASTER-PROMPT.md` — the full 5-phase run.
- `ONE-COMMAND-START.md` — short version for subsequent runs.

## Security

Never paste account numbers, passwords, or API keys into prompts or into
`COMPANY.md`.

## Disclaimer

Educational research system only — not financial, investment, tax, or legal
advice, and not a recommendation to buy or sell any security. AI output can be
wrong or out of date. Every decision stays with a human; consider a licensed
professional.

The frameworks are inspired by publicly available investing principles
associated with Warren Buffett, Ray Dalio, Peter Lynch, and Howard Marks. None
of them created, trained, approved, endorsed, or are affiliated with this
system.
