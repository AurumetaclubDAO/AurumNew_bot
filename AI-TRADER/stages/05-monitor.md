# ETAP 05 · MONITORING LOOP

Wejście: aktywne setupy z `setups/` + świeże dane. Wynik: aktualizacja plików setupów.

---

Ten etap odpalasz przy **każdym kolejnym przebiegu**, zanim zrobisz nowy skan.
Najpierw sprawdź, co masz otwarte. Dopiero potem szukaj nowego.

## 1. Pobierz świeże dane

Dla instrumentów z aktywnych setupów — tą samą ścieżką co etap 01.
Brak danych → `NOT VERIFIED`, a setup zostaje w stanie, w jakim był. **Nie zamykaj
i nie unieważniaj setupu na podstawie braku danych.**

## 2. Dla każdego aktywnego setupu ustal status

| Status | Warunek |
|---|---|
| `PENDING` | warunek wejścia jeszcze nie spełniony, teza aktualna |
| `TRIGGERED` | warunek wejścia spełniony — zapisz cenę i czas |
| `INVALIDATED` | cena unieważnienia dotknięta — setup martwy, zamknij plik |
| `EXPIRED` | minęła ważność (zamknięcie świecy z etapu 03) bez triggera |
| `TP1 HIT` / `TP2 HIT` | cel osiągnięty — zapisz cenę i czas |
| `STOPPED` | stop dotknięty — zapisz cenę i czas |

Każda zmiana statusu → wpis w `journal/TRADE-LOG.md` **tego samego dnia**.

## 3. Raport zmian

```
CO SIĘ ZMIENIŁO OD OSTATNIEGO PRZEBIEGU:
  - instrument, co konkretnie, z liczbami

STATUSY SETUPÓW:
  - ticker → status → cena/czas

RYZYKO TERAZ:
  - ryzyko łączne otwartych: X % (limit 5 %)
  - strata dzienna: X % (limit −4 %)
  - strata tygodniowa: X % (limit −8 %)
  - liczba pozycji: X (limit 3) / skorelowanych: X (limit 2)

ALERTY DO USTAWIENIA NA TRADINGVIEW:
  - konkretna cena + instrument + co oznacza

WATCHLISTA — propozycje zmian:
  - dodać / usunąć + powód
```

## 4. Twarde zasady

- **Zero prognoz.** Raportujesz, co się stało, nie co się stanie.
- Setup `INVALIDATED` jest martwy. Nie reaktywuj go, bo „cena wróciła".
  Nowa okazja = nowy setup, od etapu 01.
- **Nie uśredniamy.** Jeśli pozycja idzie przeciw tezie — to jest stop, nie dokupka.
- Jeśli ryzyko łączne albo limit straty jest przekroczony — pisz to **na górze
  raportu**, nie w środku. To informacja blokująca nowe wejścia.

## O „24/7"

Ta pętla działa wtedy, kiedy ją odpalisz. Żeby chodziła sama, potrzebujesz
harmonogramu (cron / scheduled task) + hostingu + działającego feedu danych.
**Dopóki tego nie zbudujesz — nie zakładaj, że system patrzy na rynek, gdy śpisz.**

Rekomendowany rytm ręczny: 1× przed otwarciem sesji US, 1× po zamknięciu.
