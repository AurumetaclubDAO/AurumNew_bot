# COMPANY RESEARCH

One company per research run. Every agent reads this same file and the same
source set.

COMPANY: [ ]
TICKER: [ ]
INDUSTRY: [ ]
RESEARCH DATE: [ ]
RESEARCH GOAL: [ ]
TIME HORIZON: [ ]
AVAILABLE DATA: [ ]
SOURCE URLS: [ ]
FINANCIAL STATEMENTS AVAILABLE: [ ]
EARNINGS MATERIALS AVAILABLE: [ ]
MACRO DATA AVAILABLE: [ ]
PORTFOLIO CONTEXT: [OPTIONAL]
QUESTIONS I WANT ANSWERED: [ ]

---

## How to fill this in

| Field | Tip |
| --- | --- |
| AVAILABLE DATA | List what you actually put in `data/` — e.g. "FY2025 10-K, Q2 2026 earnings release + transcript". |
| SOURCE URLS | Official investor-relations page, SEC EDGAR filing links, central-bank data pages. Add the date you accessed each. |
| PORTFOLIO CONTEXT | Optional. Leave blank and the Portfolio Analyst stays conceptual. Never paste account numbers or login details. |
| QUESTIONS I WANT ANSWERED | "Is growth slowing?" "How much debt matures in 2027?" — the memo answers these or marks them `NOT VERIFIED`. |

## Flow

```
COMPANY.md + data/
   -> 6 ANALYSTS
   -> research/01-06
   -> 4 FRAMEWORKS
   -> BULL / BEAR / RISKS / OPEN QUESTIONS
   -> memos/FINAL-INVESTMENT-RESEARCH-MEMO.md
   -> HUMAN DECISION
```
