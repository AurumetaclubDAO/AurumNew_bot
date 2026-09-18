# ETAP 06 · FINAL DECISION MEMO

Wejście: plan (03) + wynik risk checku (04). Wynik: `journal/TRADE-LOG.md` + plik setupu.

---

Podsumowanie i werdykt. **Setup, który dostał BLOCKED w etapie 04, nie trafia tutaj** —
jest odrzucony wcześniej.

## Format memo

```
═══════════════════════════════════════════
DECISION MEMO · [TICKER] · [DATA/GODZINA]
═══════════════════════════════════════════

SETUP:              typ + klasa (A/B)
REŻIM RYNKU:        trend / zakres + ADX + układ EMA
SIŁA SYGNAŁU:       mocny / średni / słaby + dlaczego (z danych, nie z wrażenia)
POZIOM RYZYKA:      niski / średni / wysoki + % kapitału

PLAN:
  Kierunek / Wejście / Stop / TP1 / TP2
  R:R netto 1 : X,XX     Pozycja X,XXX     Ryzyko XX USD (X %)

INVALIDACJA:        konkretna cena + co oznacza dla tezy

RISK CHECK:         PASS — z datą i godziną
WYMAGANY WIN RATE:  XX %

FINAL STATUS:       APPROVED / WATCHLIST / REJECTED
UZASADNIENIE:       jedno zdanie, bez „raczej tak, ale uważaj"

>> PAPER ONLY · WYMAGANA AKCEPTACJA CZŁOWIEKA <<
```

## Co znaczą statusy — precyzyjnie

| Status | Znaczenie |
|---|---|
| **APPROVED** | plan przeszedł kontrolę ryzyka i jest gotowy do rozważenia. **To nie jest polecenie wejścia.** |
| **WATCHLIST** | setup sensowny, ale warunek wejścia niespełniony albo czekamy na potwierdzenie. Obserwuj. |
| **REJECTED** | setup odrzucony. Podaj powód i czego brakowało — to materiał do nauki. |

## Zasady

- Werdykt jednoznaczny. Bez hedgingu, bez „można rozważyć".
- **APPROVED ≠ wchodzimy.** Decyzję i ryzyko bierze Karol.
- Każde memo — również REJECTED — ląduje w `journal/TRADE-LOG.md`.
  Odrzucone setupy są najcenniejszym materiałem do kalibracji systemu.
- Nigdy nie kończ memo zachętą do wejścia.

## Po zamknięciu pozycji

Uzupełnij wpis w logu: wynik w R, co zadziałało, co nie, czy setup zachował się
zgodnie z tezą. Co 20 zamkniętych pozycji — przegląd: które klasy i typy setupów
faktycznie zarabiają, a które tylko wyglądają dobrze.
