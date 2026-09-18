# ETAP 04 · RISK CHECK

Wejście: plan z etapu 03. Wynik: sekcja `RISK CHECK` w pliku setupu.

---

**To jest etap z prawem weta.** Jeśli cokolwiek łamie `RISK-RULES.md` — plan jest
zablokowany i nie idzie do etapu 06.

Walidację arytmetyczną wykonuje skill `trade-plan`. Ten etap dokłada kontrolę
portfelową, której skill nie widzi: stan otwartych pozycji i limity okresowe.

## Checklista — każdy punkt TAK/NIE, bez „raczej"

```
☐ R:R netto ≥ 2,0                                      [ ]
☐ Ryzyko tej pozycji ≤ 4 % (≤ 40 USD)                  [ ]
☐ Ryzyko zgodne z klasą setupu (A→4%, B→2%)            [ ]
☐ Ryzyko łączne po dodaniu tej pozycji ≤ 5 %           [ ]
☐ Otwartych pozycji < 3                                [ ]
☐ Skorelowanych pozycji < 2                            [ ]
☐ Dzienna strata nie osiągnęła −4 %                    [ ]
☐ Tygodniowa strata nie osiągnęła −8 %                 [ ]
☐ Reżim rynku ≠ CHAOS                                  [ ]
☐ Brak okna newsowego ±30 min                          [ ]
☐ Min. wielkość kontraktu mieści się w budżecie ryzyka [ ]
☐ Stop stoi za nazwaną strukturą                       [ ]
☐ Dane instrumentu ≠ NOT VERIFIED                      [ ]
```

## Kontrola wsteczna — obowiązkowa

Przelicz: `qty × loss_per_unit` musi równać się zadeklarowanej kwocie ryzyka.
Jeśli się nie zgadza — błąd w liczeniu, nie zaokrąglenie. Popraw, zanim przepuścisz.

## Wynik

**PASS** — wszystkie punkty TAK. Plan idzie do etapu 06.

**BLOCKED** — którykolwiek punkt NIE. Podaj:
- który punkt i o ile przekroczony (liczbowo)
- co musiałoby się zmienić na rynku, żeby setup przeszedł

**Nie proponuj obejścia.** Zawężenie stopu, podniesienie limitu, „wyjątkowo tym razem"
— to nie są opcje. Etap kończy się na BLOCKED.

## Kontekst do werdyktu

Podaj wymagany win rate przy osiągniętym R:R:

| R:R netto | Break-even WR |
|---|---|
| 1 : 1,5 | > 40,0 % |
| 1 : 2,0 | > 33,3 % |
| 1 : 2,75 | > 26,7 % |
| 1 : 3,0 | > 25,0 % |

Gdy `journal/TRADE-LOG.md` ma ≥ 50 zamkniętych pozycji — zamiast progu policz
realne EV dla tego typu setupu: `EV = WR × avg_win − (1−WR) × avg_loss`.
