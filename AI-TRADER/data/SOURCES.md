# ŹRÓDŁA DANYCH

Każda dana wrażliwa na czas ma tu wpis: co, skąd, kiedy pobrane.
Bez wpisu dana jest `NOT VERIFIED`.

## Źródła stałe

| Źródło | Zakres | Status |
|---|---|---|
| TradingView MCP (lokalny, CDP :9222) | OHLCV, EMA, ADX, VWAP, wolumen | wymaga maszyny Karola z TradingView Desktop |
| TradingView CLI (`node C:/Users/karol/tradingview-mcp/src/cli/index.js`) | jw., fallback gdy MCP nie załadowany | jw. |
| Ręczne wklejenie przez Karola | dowolne | zawsze dostępne |

**Uwaga:** w sesjach zdalnych (Claude Code na webie, Cowork bez dostępu do pulpitu)
MCP i CLI **nie działają**. Wtedy jedyna ścieżka to wklejenie danych.

## Log pobrań

| Data / godzina | Instrument | TF | Co pobrano | Źródło |
|---|---|---|---|---|
| | | | | |

## Kalendarz makro

Okna newsowe sprawdzaj przed każdym skanem (CPI, PPI, FOMC, NFP, wyniki top-5 NAS100).
Źródło kalendarza: `NOT VERIFIED` — uzupełnij o link, którego faktycznie używasz.
