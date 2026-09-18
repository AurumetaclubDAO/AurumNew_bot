# ETAP 03 · TRADE PLAN

Wejście: setup klasy A lub B z etapu 02. Wynik: `setups/YYYY-MM-DD-TICKER.md`

---

**Ten etap wykonuje skill `trade-plan`.** Nie powielaj jego logiki — wywołaj go.

Skill odpowiada za: wyznaczenie stopu za strukturą, arytmetykę kosztów, R:R netto,
wielkość pozycji i próg NO TRADE. Ten plik mówi tylko, co mu podać i co musi wrócić.

## Co podajesz skillowi

| Dana | Skąd |
|---|---|
| Ticker + interwał | etap 02 |
| Kapitał konta | `RISK-RULES.md` → 1 000 USD |
| % ryzyka | klasa setupu: A → do 4 %, B → 2 % |
| Wejście | warunek wyzwalający z etapu 02 |
| Stop | **skill wyznacza za strukturą** — nie podawaj gotowego |
| Cele TP1/TP2 | kolejne poziomy struktury z etapu 01 |
| Prowizja / slippage | `RISK-RULES.md` → 0,05 % / 0,05 % |

## Co musi wrócić

```
ASSET:
DIRECTION:          LONG / SHORT
ENTRY:              cena + warunek wyzwalający
TARGET:             TP1 / TP2
STOP:               cena + NAZWANA struktura, za którą stoi
INVALIDATION:       cena + co ona oznacza dla tezy
TIMEFRAME:          TF + ważność (do zamknięcia której świecy)
R:R NETTO:          1 : X,XX  (brutto 1 : X,XX)
POZYCJA:            X,XXX jednostek
RYZYKO:             XX USD (X % kapitału)
NOMINAŁ:            XXX USD
MATEMATYKA:         wzór z podstawionymi liczbami
POWÓD SETUPU:       jedna linia
```

## Zasady

- **Stop przed matematyką.** Stop wynika ze struktury, nie z docelowego R:R.
- Stop zawężony, żeby dopiąć R:R, to nie jest plan — to jest życzenie. `trade-plan`
  odrzuca takie przypadki i ten etap ma je przepuścić do odrzucenia.
- Arytmetykę licz w kodzie (python/bash), nie w głowie.
- Jeden setup = jeden plik w `setups/`. Bez zbiorczych plików.
- Plan jest **paper-only** i nie jest decyzją. Decyzja jest w etapie 06.
