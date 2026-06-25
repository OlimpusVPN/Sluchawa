# Teardown / analiza oryginału (ze zdjęć)

Analiza fotografii oryginalnego urządzenia („sprytna słuchawka" / pętla indukcyjna),
na podstawie której powstał [`BUILD.md`](../BUILD.md). Sekcja służy jako referencja 1:1.

> **Uwaga:** same pliki zdjęć nie są tu zapisane (zostały wklejone w czacie, nie jako pliki).
> Wrzuć je do [`reference/photos/`](photos/) wg konwencji nazw z [photos/README.md](photos/README.md).
> Poniżej spisana jest cała widoczna na nich treść.

## 1. Co widać na zdjęciach (inwentarz)

- **Ujęcie ogólne (na podłodze):** cały zestaw rozłożony:
  - czarny kabel zakończony **wtykiem minijack 3,5 mm** (TRRS) — do telefonu,
  - na tym czarnym kablu **mała zielona płytka inline** = moduł mikrofonu,
  - centralny **biały moduł** (zalany, ze wzmacniaczem) — węzeł łączący wszystko,
  - osobny czarny kabel zakończony **wtykiem USB-A** — zasilanie z powerbanku,
  - **biały przewód po prawej** zwinięty w **pętlę** = pętla indukcyjna na szyję.
- **Zbliżenia modułu:** płytka wzmacniacza OEP, niebieski rezystor, cienkie przewody
  (czerwony/czarny) od strony audio, biała litza pętli od strony wyjścia, dużo kleju na gorąco.

## 2. Płytka wzmacniacza — odczytane nadruki

- Marka/logo: **OEP**
- Oznaczenie płytki: **SHY-10282**
- Napięcie: **DC 3–5V**
- Moc: **5V@2R 5W** oraz **5V@4R 3W** (5 W na 2 Ω, 3 W na 4 Ω przy 5 V)
- Układ: **8-pinowy SOIC** (widoczny na ujęciu od spodu) → rodzina **XPT8871 / TC8871 / 8871**
  (mono, mostek BTL, klasa AB/D)
- **Niebieski rezystor** (góra płytki) = rezystor wejściowy **Ri** (ustawia wzmocnienie, Av = 2·Rf/Ri)

**Piny (dolny rząd, od lewej):** `CS · AB · IN+ · GND · VCC · SP+ · SP-`
(zgodne z opisem w BUILD.md sek. 4).

## 3. Połączenia (jak zlutowane na oryginale)

| Sygnał | Kolor / przewód na zdjęciu | Pad płytki |
|---|---|---|
| Audio IN | cienki **czerwony** (od strony czarnego kabla / jacka) | `IN+` |
| Masa | cienki **czarny** | `GND` |
| Zasilanie +5 V | z kabla USB-A | `VCC` |
| Masa zasilania | z kabla USB-A | `GND` (wspólna) |
| Pętla (2 końce) | **biała litza** (wiązka cienkich drutów Cu) | `SP+` i `SP-` |

- `CS` i `AB` — na oryginale ustawione na stałe (ukryte pod klejem); w naszej budowie:
  `CS→VCC` (włączony), `AB→GND` (klasa AB).
- Wszystkie złącza **zalane klejem na gorąco** (białe blobki) = odciążenie i ochrona cienkich drutów.

## 4. ⭐ Kluczowy szczegół: pętla z litzy (wielodrut), nie pojedynczy drut

Na zbliżeniach widać wyraźnie, że biały przewód pętli rozdziela się na **wiązkę wielu bardzo
cienkich, emaliowanych drucików miedzianych (litza)** — nie jeden drut 0,3 mm. To istotna korekta
względem pierwotnej propozycji w BUILD.md:

- **Zaleta litzy:** elastyczna, wygodna na szyję, daje dużo „efektywnych zwojów"/przekroju przy małej
  sztywności; dobrze sprzęga się magnetycznie.
- **Implikacja dla budowy 1:1:** zamiast (albo obok) drutu 0,3 mm warto użyć **cienkiego drutu
  nawojowego 0,1–0,2 mm i spleść kilka żył** (albo gotowej litzy), nawinąć kilka zwojów na szyję i
  zakończyć tak jak na zdjęciu (skręcone, pocynowane, zalane klejem).
- **Dopasowanie:** wiązka cienkich drutów ma wyższą rezystancję niż goła pętla z grubego drutu, więc
  **rezystor balastowy może być mniejszy lub zbędny** — to potwierdzamy pomiarem rezystancji gotowej
  pętli (cel: żeby wzmacniacz „widział" ~2–8 Ω). Patrz BUILD.md sek. 5.

## 5. Potwierdzone vs do zmierzenia na egzemplarzu

- ✅ Potwierdzone wizualnie: marka/model płytki, parametry, układ 8-pin, kolejność pinów, niebieski
  rezystor = Ri, pętla = litza, klej jako odciążenie, tor: jack(+mic) → moduł → pętla, USB → moduł.
- 🔍 Do zmierzenia/ustalenia przy odtwarzaniu: dokładna wartość Ri (multimetr), liczba zwojów i
  rezystancja pętli, wartość ewentualnego balastu, norma CTIA/OMTP wtyku, czy zielona płytka to sam
  mikrofon (najpewniej tak).

## 6. Powiązanie z planem budowy

Cała reszta (schemat pin-po-pinie, BOM z linkami, zasilanie + keep-alive, strojenie, błędy,
bezpieczeństwo) jest w [`BUILD.md`](../BUILD.md). Ten plik to warstwa „co dokładnie widać na
oryginale", żeby odtworzyć go wiernie.
