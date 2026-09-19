# RISK RULES — plik, który blokuje

To jedyny plik w tym systemie, którego wartości **nie wolno zmyślić ani obejść**.
Etap 04 czyta go i odrzuca każdy plan, który łamie którykolwiek próg.

---

## Kapitał i ryzyko

| Parametr | Wartość | Źródło |
|---|---|---|
| Kapitał (paper) | **1 000 USD** | Karol |
| Ryzyko max na trade | **4,0 %** = 40 USD | Karol (twardy sufit) |
| Ryzyko domyślne na trade | **2,0 %** = 20 USD | rekomendacja — patrz niżej |
| Min. R:R netto (po kosztach) | **2,0** | skill `trade-plan` |
| Max ryzyko łączne otwartych pozycji | **5,0 %** = 50 USD | skill `trade-plan` |
| Max otwartych pozycji | **3** | skill `trade-plan` |
| Max pozycji skorelowanych | **2** | skill `trade-plan` |
| Dzienny limit straty | **−4,0 %** = −40 USD | wyprowadzone (patrz konflikt A) |
| Tygodniowy limit straty | **−8,0 %** = −80 USD | wyprowadzone |
| Prowizja (jedna strona) | 0,05 % | domyślna z `trade-plan` |
| Slippage | 0,05 % | domyślna z `trade-plan` |

---

## Konflikty wynikające z ryzyka 4 %

### A. 4 % na trade vs. −3 % dzienny limit — ✅ ROZSTRZYGNIĘTE
Domyślny dzienny limit w skillu `trade-plan` to −3 %. Przy ryzyku 4 % na trade
**jedna stratna transakcja od razu go przekracza** — limit blokowałby system, zanim
zdążyłby cokolwiek zrobić. Rozstrzygnięcie: dzienny limit podniesiony do **−4 %**,
czyli równo jedno pełne ryzyko maksymalne. Po jednym pełnym stopie — koniec dnia.

**Zaakceptowane przez Karola 2026-09-19.** Limit −4 % obowiązuje i nie jest już
otwartą kwestią — etap 04 egzekwuje go bez pytania.

### B. 4 % na trade vs. 5 % ekspozycji łącznej
Przy 4 % na trade **możesz mieć realnie jedną otwartą pozycję** (4 % + 4 % = 8 % > 5 %).
Limity „max 3 pozycje" i „max 2 skorelowane" aktywują się dopiero przy ryzyku ≤ 2,5 %.
To nie jest błąd — to konsekwencja. Chcesz grać wielopozycyjnie → zejdź do 1,5–2 %.

### C. Wielkość kontraktu vs. 1 000 USD
Przy koncie 1 000 USD minimalna wielkość kontraktu u brokera może **wymusić ryzyko
wyższe niż 40 USD** (typowe na indeksach i złocie). Jeżeli min. krok instrumentu nie
mieści się w budżecie ryzyka — to jest `NO TRADE`, a nie powód do zawężenia stopu.
Etap 04 ma to sprawdzać jawnie.

---

## Rekomendacja — i dlaczego

Sufit 4 % zostaje jako Twoja decyzja. Ale domyślnie licz **2 %**, bo arytmetyka serii
strat jest bezlitosna:

| Seria 5 strat pod rząd | Kapitał po | Obsunięcie | Potrzebny zwrot do odrobienia |
|---|---|---|---|
| przy 4 % | 815 USD | **−18,5 %** | +22,6 % |
| przy 2 % | 904 USD | −9,6 % | +10,6 % |

Pięć strat pod rząd przy R:R 2,0 i win rate 40 % to zdarzenie całkowicie normalne —
zdarza się średnio raz na kilkadziesiąt transakcji. Przy 4 % kosztuje prawie jedną
piątą konta.

**4 % używaj tylko dla setupów klasy A** (zgodność HTF+LTF, ADX > 25, potwierdzenie
wolumenem, R:R netto ≥ 3,0). Wszystko inne — 2 %.

---

## Twarde blokady (etap 04 zwraca NO TRADE)

- `rr_netto < 2,0`
- ryzyko tej pozycji > 4 % kapitału
- ryzyko łączne otwartych pozycji po dodaniu tej > 5 %
- już 3 otwarte pozycje, albo 2 skorelowane
- dzienna strata osiągnęła −4 %, tygodniowa −8 %
- reżim rynku = CHAOS (ATR > 90. percentyla, luka > 2 ATR, okno newsowe)
- minimalna wielkość kontraktu wymusza ryzyko > 4 %
- stop nie stoi za żadną nazwaną strukturą
- brak zweryfikowanych danych dla instrumentu (`NOT VERIFIED`)

Przy NO TRADE **nie proponuj wariantu „ale gdyby stop był ciaśniejszy".**
Napisz, czego brakuje, i zakończ.

---

## Korelacje — traktuj jako jedną pozycję

| Grupa | Instrumenty |
|---|---|
| Krypto beta | BTC, ETH i altcoiny — zawsze skorelowane |
| Indeksy US | NAS100, SP500, US30 |
| Ryzyko/dolar | XAUUSD vs indeksy — korelacja zmienna, sprawdzaj przed drugą pozycją |

---

## Zmiana tych wartości

Tylko Karol. Claude nigdy nie podnosi limitu, żeby plan przeszedł walidację.
Każda zmiana + data w `journal/TRADE-LOG.md`.
