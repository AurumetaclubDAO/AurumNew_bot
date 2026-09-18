# MASTER PROMPT — pełny przebieg

Wklej to w Claude Code po `cd AI-TRADER && claude`.
Przy kolejnych przebiegach wystarczy `ONE-COMMAND-START.md`.

---

```
Uruchom pętlę AI Trader.

ZANIM ZACZNIESZ:
1. Przeczytaj CLAUDE.md — to reguły twarde, nie sugestie.
2. Przeczytaj RISK-RULES.md — limity są nienegocjowalne.
3. Przeczytaj WATCHLIST.md — instrumenty i interwały.
4. Sprawdź dostęp do danych: TradingView MCP → CLI → poproś mnie o wklejenie.
   Nie zgaduj żadnej ceny ani wartości wskaźnika.

NASTĘPNIE WYKONAJ PO KOLEI:

ETAP 05 — MONITORING (pomiń przy pierwszym uruchomieniu)
  stages/05-monitor.md
  Najpierw sprawdź aktywne setupy w setups/. Dopiero potem szukaj nowych.
  Zaraportuj stan ryzyka na górze.

ETAP 01 — SCAN
  stages/01-scan.md
  Zapisz: data/snapshots/YYYY-MM-DD-HHMM-scan.md
  Braki danych oznacz NOT VERIFIED i wypisz listą.

ETAP 02 — SYGNAŁY
  stages/02-signals.md
  Przypisz klasę A/B/C. Klasa C nie idzie dalej.
  Brak setupów to poprawny wynik — nie produkuj ich na siłę.

ETAP 03 — PLAN TRANSAKCJI  (dla każdego setupu klasy A lub B)
  stages/03-trade-plan.md
  Użyj skilla trade-plan. Stop wyznacz za strukturą PRZED liczeniem R:R.
  Zapisz: setups/YYYY-MM-DD-TICKER.md

ETAP 04 — KONTROLA RYZYKA
  stages/04-risk-check.md
  Przejdź całą checklistę. Przy złamaniu któregokolwiek limitu: BLOCKED,
  bez propozycji obejścia. Wykonaj kontrolę wsteczną qty × loss_per_unit.

ETAP 06 — MEMO DECYZYJNE  (tylko dla planów z PASS)
  stages/06-decision.md
  Werdykt: APPROVED / WATCHLIST / REJECTED.
  Zapisz każde memo, również REJECTED, do journal/TRADE-LOG.md

NA KONIEC ZWRÓĆ:
  - ile instrumentów przeskanowano, ile z brakami danych
  - ile setupów znaleziono, w podziale na klasy
  - ile przeszło risk check, ile zablokowanych i dlaczego
  - stan ryzyka: łączne / dzienne / tygodniowe
  - co wymaga mojej decyzji

CZEGO NIE ROBISZ:
  - nie składasz zleceń, nie łączysz się z brokerem
  - nie zmyślasz cen, wskaźników ani newsów
  - nie podnosisz limitu ryzyka, żeby plan przeszedł
  - nie dajesz ślepego sygnału kupuj/sprzedaj bez invalidacji
  - nie kończysz zachętą do wejścia

To jest paper trading. Decyzja i ryzyko są moje.
```
