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

**Źródło:** https://www.forexfactory.com/calendar
Potwierdzone przez Karola 2026-09-19.

Sprawdzaj **przed każdym skanem**, nie po. Zasada z `WATCHLIST.md`:
**30 min przed i 30 min po publikacji — brak nowych wejść.**

### Jak filtrować

ForexFactory domyślnie pokazuje wszystko. Ustaw filtry raz — zapisują się w sesji:

| Filtr | Ustawienie | Dlaczego |
|---|---|---|
| Impact | tylko **czerwone** (high) | pomarańczowe i żółte nie ruszają indeksów ani złota na tyle, żeby blokować wejście |
| Currency | **USD** | cała watchlista (krypto, XAUUSD, USOIL, NAS100, SP500) reaguje na dolara i Fed |
| Timezone | ustaw swoją strefę | inaczej pomylisz godzinę publikacji, a liczy się okno ±30 min |

### Co blokuje wejście

- CPI / PPI US
- decyzja FOMC + konferencja prasowa
- NFP (pierwszy piątek miesiąca)
- PKB US, sprzedaż detaliczna, PCE

### Czego ForexFactory NIE pokaże

**Wyników spółek z top-5 wagi NAS100.** To osobne źródło — sprawdzaj kalendarz
earnings u brokera albo na TradingView. `NOT VERIFIED` — uzupełnij, jeśli zaczniesz
grać NAS100 w sezonie wynikowym.

Dla krypto ForexFactory też nie pokrywa zdarzeń on-chain (unlocki, hardforki,
decyzje regulacyjne). Przy BTCUSD/ETHUSD traktuj to jako lukę, nie jako brak ryzyka.
