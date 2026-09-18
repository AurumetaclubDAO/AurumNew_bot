# WATCHLIST

Trzy koszyki. **Max 6 instrumentów aktywnie obserwowanych naraz** — więcej i etap 01
przestaje być skanem, a staje się szumem.

---

## Interwały

| Rola | TF | Do czego |
|---|---|---|
| HTF | **D1** | kierunek trendu, główna struktura |
| HTF zapasowy | H4 | gdy za mało historii na D1 |
| LTF | **H1** | strefa wejścia, potwierdzenie |
| LTF precyzyjny | M15 | dokładny trigger wejścia |

Zgodne z domyślnymi w skillu `tradingview-ema`.
`ASSUMPTION — NOT FACT`: Karol nie podał interwałów, przyjęto domyślne. Zmień, jeśli
pracujesz na innych.

---

## Koszyk 1 — KRYPTO

| Symbol | Uwagi |
|---|---|
| BTCUSD | benchmark reżimu całego koszyka — czytaj go zawsze pierwszy |
| ETHUSD | skorelowany z BTC → liczy się jako ta sama pozycja |

Sesja: 24/7. Największa zmienność: otwarcie US (14:30–16:00 CET) i azjatycki poranek.

## Koszyk 2 — SUROWCE

| Symbol | Uwagi |
|---|---|
| XAUUSD | złoto — reaguje na realne stopy i DXY, nie na „strach" |
| USOIL | ropa — ryzyko luk na newsach geopolitycznych, szerokie stopy |

Sesja: płynność w godzinach London + NY. Poza nimi spready rosną.

## Koszyk 3 — INDEKSY

| Symbol | Uwagi |
|---|---|
| NAS100 | najwyższa zmienność z indeksów, mocna korelacja z sentymentem tech |
| US500 | szerszy rynek — skorelowany z NAS100, licz jako jedną pozycję |

Sesja: 15:30–22:00 CET (cash session). Poza nią — tylko obserwacja, nie wejścia.

---

## Symbole brokera

Skille wskazują, że pracujesz na symbolach **VANTAGE** (NAS100, ETHUSD).
`NOT VERIFIED` — potwierdź dokładne tickery dla XAUUSD, USOIL, US500, BTCUSD
u swojego brokera i podmień w tabelach powyżej, zanim pierwszy raz odpalisz skan.
Zły ticker = dane z innego instrumentu = cały run do kosza.

---

## Okna newsowe — twarde „nie wchodzę"

Etap 04 traktuje reżim CHAOS jako blokadę. Sprawdź kalendarz przed skanem:

- CPI / PPI US
- decyzja FOMC + konferencja
- NFP (pierwszy piątek miesiąca)
- wyniki spółek z top-5 wagi NAS100

Zasada: **30 min przed i 30 min po** — brak nowych wejść.

---

## Rotacja

Instrument, który przez 10 kolejnych skanów nie wygenerował ani jednego setupu
z R:R netto ≥ 2,0 — wypada z watchlisty na miesiąc. Zapisz to w `journal/TRADE-LOG.md`.
