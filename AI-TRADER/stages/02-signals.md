# ETAP 02 · SIGNAL DETECTION

Wejście: wynik etapu 01. Wynik: sekcja `SYGNAŁY` w tym samym snapshocie.

---

Ze zeskanowanych danych wyłap **możliwe** setupy. Nie transakcje — możliwości.

## Typy setupów

| Typ | Warunek bazowy |
|---|---|
| Breakout | wybicie poziomu z potwierdzeniem wolumenu |
| Pullback | korekta do EMA20/50 lub strefy w trendzie zgodnym z HTF |
| Momentum | rozszerzenie EMA + ADX rosnący powyżej 25 |
| Kontynuacja trendu | nowy HH/LL po konsolidacji, struktura nienaruszona |
| Odwrócenie | złamanie struktury (HL→LL lub LH→HH) + dywergencja wolumenu |

## Dla każdego setupu podaj

```
INSTRUMENT / TF:
TYP SETUPU:
DOWODY:            2-3 konkretne obserwacje z danych etapu 01 — z liczbami
CO POTWIERDZI:     konkretne zdarzenie cenowe (nie „siła")
CO UNIEWAŻNI:      konkretna cena
ZGODNOŚĆ HTF/LTF:  zgodne / rozjazd — rozjazd obniża klasę setupu
POZYCJA W ZAKRESIE: X% — z etapu 01, decyduje o dopuszczeniu (patrz filtr niżej)
KLASA:             A / B / C
```

## Filtr pozycji w zakresie — stosuj PRZED klasyfikacją

```
pozycja = (cena − HL) / (HH − HL) × 100%
```

**To jest filtr, nie ciekawostka.** Przy TP na przeciwległym ekstremum i stopie za
najbliższym, R:R brutto spada poniżej 2,0 dokładnie na **33,3% zakresu** — i to
jeszcze bez bufora ATR i bez kosztów. Z nimi realny próg wypada w okolicach **24%**.

| Pozycja (long) | Werdykt |
|---|---|
| ≤ 25% | wykonalny — stop krótki, cel daleko |
| 25–33% | graniczny — policz R:R netto, zwykle wypada 1,4–2,0 |
| **> 33%** | **klasa C automatycznie — nie przepuszczaj dalej** |

Short odwrotnie: ≥ 75% wykonalny, 67–75% graniczny, **< 67% klasa C**.

**Wyjątek — wybicie.** Gdy cena wybija HH (long) lub LL (short) z potwierdzeniem
wolumenu, nie grasz w tym zakresie tylko otwierasz nowy. Filtr się nie stosuje, ale
TP wyznacz z rozszerzenia, nie z pokonanego ekstremum.

**Po co to.** Setup w środku zakresu wygląda dobrze na wykresie — trend zgodny,
wolumen rośnie, EMA ułożone — i przechodzi przez etapy 03 i 04, żeby dopiero tam
polec na R:R. To spalony czas i pokusa, żeby „poprawić" stop. Odrzuć go tutaj.

---

## Klasy setupów — decydują o ryzyku w etapie 04

| Klasa | Kryteria |
|---|---|
| **A** | HTF i LTF zgodne, ADX > 25, potwierdzenie wolumenem, czysta struktura |
| **B** | zgodność kierunku, ale jedno kryterium kuleje |
| **C** | kontra do HTF, albo ADX < 20, albo brak potwierdzenia wolumenem, albo **pozycja w zakresie > 33%** (long) / < 67% (short) |

Klasa A → dopuszczalne ryzyko do 4 %. Klasa B → 2 %. **Klasa C → nie przechodzi dalej.**

## Zasady

- To są **możliwe** setupy, nie gwarantowane transakcje. Formułuj warunkowo.
- Setup bez konkretnej ceny unieważnienia nie jest setupem — odrzuć go tutaj.
- **Nie produkuj setupów na siłę.** „Brak setupów w tym skanie" to poprawny,
  częsty i wartościowy wynik. Rynek jest w zakresie przez większość czasu.
- Nie oceniaj tu ryzyka ani wielkości pozycji. Od tego jest etap 04.
