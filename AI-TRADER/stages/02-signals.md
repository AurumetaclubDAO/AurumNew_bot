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
KLASA:             A / B / C
```

## Klasy setupów — decydują o ryzyku w etapie 04

| Klasa | Kryteria |
|---|---|
| **A** | HTF i LTF zgodne, ADX > 25, potwierdzenie wolumenem, czysta struktura |
| **B** | zgodność kierunku, ale jedno kryterium kuleje |
| **C** | kontra do HTF, albo ADX < 20, albo brak potwierdzenia wolumenem |

Klasa A → dopuszczalne ryzyko do 4 %. Klasa B → 2 %. **Klasa C → nie przechodzi dalej.**

## Zasady

- To są **możliwe** setupy, nie gwarantowane transakcje. Formułuj warunkowo.
- Setup bez konkretnej ceny unieważnienia nie jest setupem — odrzuć go tutaj.
- **Nie produkuj setupów na siłę.** „Brak setupów w tym skanie" to poprawny,
  częsty i wartościowy wynik. Rynek jest w zakresie przez większość czasu.
- Nie oceniaj tu ryzyka ani wielkości pozycji. Od tego jest etap 04.
