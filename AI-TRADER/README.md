# AI TRADER

Pętla monitoringu rynku: **Scan → Signals → Trade Plan → Risk Check → Monitor → Decision.**

Struktura odwzorowana z guide'a "How to Build a 24/7 AI Trader with Fable 5" (@seb.ai),
ale etapy 01/03/04 delegują do gotowych skilli Karola (`tradingview-ema`, `trade-plan`)
zamiast wklejania danych ręcznie.

**To nie jest bot.** Nie składa zleceń, nie łączy się z brokerem, nie ma dostępu do
konta. Produkuje memo decyzyjne — decyzję podejmuje człowiek. Paper only.

## Struktura

```
AI-TRADER/
├── CLAUDE.md               reguły twarde — czytane w każdej sesji
├── WATCHLIST.md            krypto / surowce / indeksy + interwały
├── RISK-RULES.md           kapitał, limity, blokady — plik z prawem weta
├── MASTER-PROMPT.md        pełny przebieg 6 etapów
├── ONE-COMMAND-START.md    skrót na kolejne uruchomienia
│
├── stages/                 01-scan … 06-decision
├── data/
│   ├── snapshots/          surowe skany per przebieg (gitignored)
│   └── SOURCES.md          co, skąd, kiedy pobrane
├── setups/                 aktywne plany transakcji (paper)
├── journal/TRADE-LOG.md    log każdej decyzji + wyniki
└── templates/              plan / memo / wpis do dziennika
```

## Jak uruchomić

1. Potwierdź tickery brokera w `WATCHLIST.md` (obecnie `NOT VERIFIED`).
2. Sprawdź `RISK-RULES.md` — szczególnie sekcję konfliktów A/B/C.
3. `cd AI-TRADER && claude`
4. Wklej `MASTER-PROMPT.md`. Przy kolejnych przebiegach — `ONE-COMMAND-START.md`.

## Dane

| Ścieżka | Kiedy działa |
|---|---|
| TradingView MCP | sesja na maszynie Karola, TradingView Desktop na porcie 9222 |
| TradingView CLI | jw., gdy MCP nie załadowany w sesji |
| Ręczne wklejenie | zawsze — jedyna ścieżka w sesjach zdalnych |

Czego nie da się pobrać → `NOT VERIFIED`. Nigdy zgadywanie.

## Parametry (stan na start)

| | |
|---|---|
| Rynki | krypto · surowce · indeksy |
| Interwały | HTF D1 · LTF H1 |
| Kapitał (paper) | 1 000 USD |
| Ryzyko max / domyślne | 4 % / 2 % |
| Min. R:R netto | 2,0 |

## O „24/7"

Pętla chodzi wtedy, kiedy ją odpalisz. Prawdziwe 24/7 wymaga harmonogramu, hostingu
i działającego feedu danych — tego tu nie ma i **nie buduj tego, zanim nie zbierzesz
30+ wpisów w `journal/TRADE-LOG.md`.** Najpierw sprawdź, czy setupy w ogóle działają.

## Disclaimer

System edukacyjno-analityczny. Nie stanowi doradztwa inwestycyjnego, finansowego,
podatkowego ani prawnego i nie jest rekomendacją kupna lub sprzedaży jakiegokolwiek
instrumentu. Wyniki AI mogą być błędne lub nieaktualne. Trading niesie realne ryzyko
straty kapitału. Każda decyzja pozostaje po stronie człowieka.
