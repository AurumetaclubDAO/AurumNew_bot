# AurumNew_bot — systemy analityczne dla Claude Code

Dwa niezależne moduły. Żaden z nich nie składa zleceń i nie łączy się z brokerem.
Oba kończą się dokumentem, a decyzję podejmuje człowiek.

| Moduł | Do czego | Horyzont |
|---|---|---|
| [`AI-INVESTMENT-TEAM/`](AI-INVESTMENT-TEAM/) | research fundamentalny spółki → memo inwestycyjne | długi |
| [`AI-TRADER/`](AI-TRADER/README.md) | pętla monitoringu rynku → memo decyzyjne (paper) | krótki / swing |

---

# 1. AI Investment Team

Struktura research'u inwestycyjnego dla Claude Code, odwzorowana 1:1 z guide'a
"Build Your AI Investment Team" (@seb.ai).

**To jest system badawczy, nie system inwestycyjny.** Nie generuje sygnałów
kupna/sprzedaży, nie łączy się z brokerem, nie wykonuje transakcji. Produkuje
jeden dokument — memo — a decyzję podejmuje człowiek.

## Struktura

```
AI-INVESTMENT-TEAM/
├── CLAUDE.md                  reguły, które Claude Code czyta w każdej sesji
├── COMPANY.md                 jedna spółka na jeden research run
├── MASTER-PROMPT.md           pełny przebieg w 5 fazach
├── ONE-COMMAND-START.md       skrócona wersja na kolejne uruchomienia
│
├── data/
│   ├── financials/            sprawozdania, które sam dostarczasz (10-K, 10-Q)
│   ├── earnings/              raporty kwartalne, transkrypty, slajdy
│   ├── filings/               pozostałe dokumenty regulacyjne
│   ├── macro/                 stopy, inflacja, PKB
│   └── sources/SOURCES.md     URL-e + daty dostępu do wszystkiego powyżej
│
├── analysts/                  6 promptów analityków
├── frameworks/                4 prompty frameworków
├── research/                  tu każdy analityk zapisuje swój plik (01–06)
├── memos/                     tu ląduje FINAL-INVESTMENT-RESEARCH-MEMO.md
└── templates/                 szkielet memo + checklista końcowa
```

## Jak uruchomić

1. Wypełnij `AI-INVESTMENT-TEAM/COMPANY.md` — jedna spółka.
2. Wrzuć zweryfikowane materiały do `AI-INVESTMENT-TEAM/data/` i wpisz każde
   źródło z datą do `data/sources/SOURCES.md`.
3. `cd AI-INVESTMENT-TEAM && claude`
4. Wklej treść `MASTER-PROMPT.md`.
5. Przy kolejnych spółkach wystarczy `ONE-COMMAND-START.md`.

## Przepływ

```
COMPANY.md + data/
  -> 6 analityków  -> research/01-06
  -> 4 frameworki  -> te same dowody, cztery soczewki
  -> BULL / BEAR / RYZYKA / OTWARTE PYTANIA
  -> memos/FINAL-INVESTMENT-RESEARCH-MEMO.md
  -> DECYZJA CZŁOWIEKA
```

## Ograniczenie, o którym trzeba wiedzieć przed pierwszym uruchomieniem

Claude Code **nie ma** automatycznego dostępu do aktualnych cen, filingów SEC,
wyników kwartalnych, danych makro, newsów, estymat analityków ani Twojego
portfela.

Żeby system operował na prawdziwych danych, trzeba albo:

- podłączyć legalne źródło — API, serwer MCP, narzędzie wyszukiwania/przeglądarkę
  lub konektor, albo
- wkleić dane ręcznie razem ze źródłem i datą.

Bez tego memo powstanie, ale będzie oparte wyłącznie na tym, co sam włożysz do
`data/`. Wszystko, czego nie da się zweryfikować, ma być oznaczone jako
`NOT VERIFIED` — nigdy zmyślone.

## Reguły systemu

- Nigdy BUY ani SELL.
- Brak danych = `NOT VERIFIED`.
- Założenie = `ASSUMPTION — NOT FACT`.
- Scenariusz = `SCENARIO — NOT PREDICTION`.
- Każde źródło wrażliwe na czas ma datę.
- FAKTY / ANALIZA / ZAŁOŻENIA / SCENARIUSZE trzymane osobno.
- Nigdy nie wklejaj do promptów numerów kont, haseł ani kluczy API.

---

# 2. AI Trader

Pętla monitoringu rynku odwzorowana z guide'a "How to Build a 24/7 AI Trader with
Fable 5" (@seb.ai), spięta z istniejącymi skillami (`tradingview-ema`, `trade-plan`)
zamiast ręcznego wklejania danych.

```
Scan -> Signals -> Trade Plan -> Risk Check -> Monitor -> Decision -> CZŁOWIEK
```

```
AI-TRADER/
├── CLAUDE.md               reguły twarde
├── WATCHLIST.md            krypto / surowce / indeksy + interwały
├── RISK-RULES.md           limity i blokady — plik z prawem weta
├── MASTER-PROMPT.md        pełny przebieg 6 etapów
├── ONE-COMMAND-START.md    skrót na kolejne uruchomienia
├── stages/                 01-scan … 06-decision
├── data/                   snapshoty skanów + SOURCES.md
├── setups/                 aktywne plany (paper)
├── journal/TRADE-LOG.md    log decyzji i wyników
└── templates/              plan / memo / wpis do dziennika
```

Start: `cd AI-TRADER && claude`, potem wklej `MASTER-PROMPT.md`.
Szczegóły i parametry ryzyka: [`AI-TRADER/README.md`](AI-TRADER/README.md).

**„24/7" jest umowne.** Pętla działa wtedy, kiedy ją odpalisz. Automatyzacja wymaga
harmonogramu, hostingu i feedu danych — i nie ma sensu przed zebraniem historii
w `journal/TRADE-LOG.md`.

## Reguły modułu tradingowego

- Nigdy nie składa zleceń, nigdy nie łączy się z brokerem. Paper only.
- Nigdy ślepego sygnału kupuj/sprzedaj — zawsze invalidacja i kontekst ryzyka.
- Limity z `RISK-RULES.md` są twarde. Złamany limit = `BLOCKED`, bez obejść.
- Stop wynika ze struktury, nie z docelowego R:R.
- Brak danych = `NOT VERIFIED`. Nigdy zgadywanie ceny ani wskaźnika.
- Klucze API wyłącznie w `.env` (gitignored).

---

# Disclaimer (dotyczy obu modułów)

Systemy wyłącznie edukacyjno-badawcze. Nie stanowią doradztwa finansowego,
inwestycyjnego, podatkowego ani prawnego i nie są rekomendacją kupna lub
sprzedaży jakiegokolwiek instrumentu. Wyniki AI mogą być błędne lub nieaktualne.
Każda decyzja pozostaje po stronie człowieka; rozważ konsultację z licencjonowanym
specjalistą.

Frameworki są inspirowane publicznie dostępnymi zasadami inwestycyjnymi
kojarzonymi z Warrenem Buffettem, Rayem Dalio, Peterem Lynchem i Howardem
Marksem. Żadna z tych osób nie stworzyła, nie zatwierdziła, nie poparła tego
systemu ani nie jest z nim w żaden sposób powiązana.

Trading niesie realne ryzyko straty kapitału. Moduł `AI-TRADER/` działa wyłącznie
w trybie paper i nie ma żadnego połączenia z rachunkiem maklerskim.

Źródła struktury: darmowe guide'y "Build Your AI Investment Team" oraz
"How to Build a 24/7 AI Trader with Fable 5" (@seb.ai).
