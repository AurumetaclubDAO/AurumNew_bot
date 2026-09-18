# TRADE PLAN · [TICKER] · [DATA]

> Paper only. Nie jest to rekomendacja ani decyzja.

## Setup

| Pole | Wartość |
|---|---|
| Instrument | |
| Klasa setupu | A / B |
| Typ setupu | |
| TF (HTF / LTF) | |
| Reżim rynku | trend / zakres + ADX + układ EMA |

## Plan

| Pole | Wartość |
|---|---|
| Kierunek | LONG / SHORT |
| Wejście | cena + warunek wyzwalający |
| Stop | cena + **nazwana struktura, za którą stoi** |
| TP1 | |
| TP2 | |
| Invalidacja | cena + co oznacza dla tezy |
| Ważność | do zamknięcia świecy [TF] dnia [data] |

## Matematyka

```
equity     =
risk_pct   =
risk_cash  =

entry_eff  =
stop_eff   =
tp_eff     =

loss_per_unit = |entry_eff - stop_eff| + entry_eff*fee + stop_eff*fee =
win_per_unit  = |tp_eff - entry_eff|   - entry_eff*fee - tp_eff*fee   =

qty       = risk_cash / loss_per_unit =
rr_netto  = win_per_unit / loss_per_unit =
rr_brutto =
notional  = qty * entry_eff =

KONTROLA WSTECZNA: qty × loss_per_unit = ____  (musi = risk_cash)
```

## Powód setupu

_Jedna linia. Konkret, nie ogólnik._

## Risk check

- [ ] status: PASS / BLOCKED
- [ ] data i godzina:
- [ ] jeśli BLOCKED — który punkt i o ile:

## Status

`PENDING` / `TRIGGERED` / `INVALIDATED` / `EXPIRED` / `TP1 HIT` / `TP2 HIT` / `STOPPED`

| Data | Zmiana statusu | Cena | Uwaga |
|---|---|---|---|
| | | | |
