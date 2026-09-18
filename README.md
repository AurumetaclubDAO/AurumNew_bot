# AI Investment Team

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

## Disclaimer

System wyłącznie edukacyjno-badawczy. Nie stanowi doradztwa finansowego,
inwestycyjnego, podatkowego ani prawnego i nie jest rekomendacją kupna lub
sprzedaży jakiegokolwiek instrumentu. Wyniki AI mogą być błędne lub nieaktualne.
Każda decyzja pozostaje po stronie człowieka; rozważ konsultację z licencjonowanym
specjalistą.

Frameworki są inspirowane publicznie dostępnymi zasadami inwestycyjnymi
kojarzonymi z Warrenem Buffettem, Rayem Dalio, Peterem Lynchem i Howardem
Marksem. Żadna z tych osób nie stworzyła, nie zatwierdziła, nie poparła tego
systemu ani nie jest z nim w żaden sposób powiązana.

Źródło struktury: darmowy guide "Build Your AI Investment Team" (@seb.ai).
