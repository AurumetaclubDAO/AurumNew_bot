# AI TRADER — REGUŁY TWARDE

System monitoringu i planowania transakcji. **Paper only.**

## Czego ten system NIE robi

- Nie składa zleceń. Nie łączy się z brokerem. Nie ma dostępu do konta.
- Nie daje ślepych sygnałów „kupuj/sprzedaj" — zawsze invalidacja + kontekst ryzyka.
- Nie przewiduje. Warianty są warunkowe: „jeśli X, to Y".

## Dane

Kolejność źródeł — bez skrótów:

1. TradingView MCP (narzędzia w sesji — sprawdź `ToolSearch` zapytaniem "tradingview")
2. TradingView CLI: `node C:/Users/karol/tradingview-mcp/src/cli/index.js <cmd>`
   (tylko na maszynie Karola, TradingView Desktop na `--remote-debugging-port=9222`)
3. Ręczne wklejenie danych przez Karola — cena, EMA20/50/200, ADX, VWAP, świece

Szczegóły składni: skill `tradingview-ema` → `references/data-access.md`
oraz `C:\Users\karol\tradingview-mcp\CLAUDE.md` (źródło prawdy dla komend).

**Jeśli wszystkie trzy zawiodą — piszesz `NOT VERIFIED`. Nigdy nie zgadujesz ceny,
wartości wskaźnika ani newsa.**

## Oznaczenia

| Znacznik | Kiedy |
|---|---|
| `NOT VERIFIED` | dana niedostępna lub niepotwierdzona |
| `ASSUMPTION — NOT FACT` | założenie własne |
| `SCENARIO — NOT PREDICTION` | wariant warunkowy |

Każda dana wrażliwa na czas ma znacznik czasu (data + godzina + TF świecy).

## Delegacja do skilli — nie powielaj logiki

| Etap | Skill |
|---|---|
| 01 Scan — dane i odczyt trendu | `tradingview-ema` |
| 03 Trade Plan — entry/stop/TP | `trade-plan` |
| 04 Risk Check — sizing, R:R netto, NO TRADE | `trade-plan` |

Etapy 02, 05, 06 są własne — nie mają odpowiednika w skillach.

## Kto decyduje

Etap 06 kończy się werdyktem APPROVED / WATCHLIST / REJECTED.
**APPROVED znaczy: plan przeszedł kontrolę ryzyka.** Nie znaczy: wchodzimy.
Decyzję i ryzyko bierze Karol.

## Bezpieczeństwo

- Klucze API tylko w `.env` (gitignored). Nigdy w promptach, nigdy w plikach repo.
- Nigdy numerów kont, haseł ani danych logowania do brokera.
- Live trading pozostaje wyłączony.

## Disclaimer

System edukacyjno-analityczny. Nie stanowi doradztwa inwestycyjnego, finansowego,
podatkowego ani prawnego i nie jest rekomendacją kupna lub sprzedaży. Wyniki AI mogą
być błędne lub nieaktualne. Trading niesie realne ryzyko straty kapitału.
