# Słuchawa — dyskretna douszna słuchawka indukcyjna (IFB) DIY

Przewodnik budowy własnej, dyskretnej dousznej słuchawki działającej na **pętli indukcyjnej** —
odpowiednika telewizyjnego **IFB** (interruptible foldback), w którym współpracownik podpowiada
mówcy do ucha podczas wystąpienia/prezentacji. To ta sama technika, której używają pętle
indukcyjne dla aparatów słuchowych (telecoil). Budujemy ją samodzielnie z tanich modułów,
odtwarzając 1:1 architekturę z dostępnych na rynku zestawów (płytka **OEP SHY‑10282 / XPT8871**,
pętla na szyję, mały magnes w uchu, zasilanie z powerbanku).

> ### ⚠️ Zanim zaczniesz — bezpieczeństwo i odpowiedzialność
> - **Ucho:** używaj magnesu na tyle dużego/wyciągalnego, by nie utknął za zwężeniem kanału
>   słuchowego; **zawsze miej mocniejszy magnes‑„wyciągacz"** i przećwicz wyciąganie *poza uchem*.
>   Nie wpychaj na siłę i nie głęboko. Jeśli coś utknie — **nie dłub, idź do laryngologa.**
> - **Magnesy:** trzymaj z dala od rozruszników serca i innych implantów; zdejmij przed badaniem MRI.
> - **Zasilanie:** używaj tylko 5 V z powerbanku/USB (nie podłączaj do sieci 230 V); nie przekraczaj
>   5,5 V na wzmacniaczu.
> - **Zastosowanie:** to projekt do legalnego, dyskretnego odsłuchu (Twoje wystąpienia, teatr, plan,
>   pomoc w słyszeniu). Używanie urządzeń do odsłuchu jako niedozwolonej pomocy na egzaminach jest
>   w Polsce zabronione i grozi unieważnieniem egzaminu.

---

## 1. Jak to działa

```
   Telefon            Wzmacniacz             Pętla na szyję          Ucho
 (audio + mic)  →   (XPT8871, 5V z   →   (drut emaliowany,   →   (magnes drga
   jack 3,5mm        powerbanku)          kilka zwojów)            w polu = dźwięk)
                                              │
                                       pole magnetyczne (pole bliskie, NIE radio)
```

- Telefon wysyła sygnał audio (głos osoby podpowiadającej) przez gniazdo 3,5 mm.
- Mały wzmacniacz mono podbija sygnał i wymusza **prąd** w pętli z drutu noszonej na szyi.
- Prąd audio w pętli tworzy **zmienne pole magnetyczne** — dokładną magnetyczną kopię dźwięku.
- W uchu siedzi **mały magnes**. Pole „szarpie" nim w rytm dźwięku — magnes drga i przekazuje
  drgania na błonę bębenkową. Słyszysz cichą mowę. Część w uchu **nie ma baterii ani elektroniki.**
- Tor mikrofonu (elektret wpięty w pin MIC jacka) sprawia, że przez zwykłe połączenie telefoniczne
  osoba podpowiadająca **słyszy Ciebie** — więc to działa dwukierunkowo.

To pole bliskie (indukcja), nie fala radiowa — dlatego zasięg „pętla→ucho" jest krótki (magnes musi
być w uchu tuż przy pętli), a „telefon→świat" jest nieograniczony (to normalna rozmowa).

---

## 2. Lista zakupowa (BOM)

Wariant **max‑DIY / najtaniej**, telefon z gniazdem 3,5 mm.

| # | Część | Parametr / czego szukać | Szt. | Gdzie kupić (przykłady) | Cena orient. |
|---|---|---|---|---|---|
| 1 | **Wzmacniacz mono** | XPT8871 / „OEP 5W", DC 3–5 V, 5 W, SOP‑8 | 1–2 | Allegro: „XPT8871", „wzmacniacz mono 5W"; [eBay](https://www.ebay.com/itm/335509230008); [Banggood 5‑pak](https://usa.banggood.com/5Pcs-XPT8871-5V-5W-1A-Single-Channel-Mono-Digital-Audio-Amplifier-Receiver-Module-Board-p-1268827.html); [Amazon 2‑pak](https://www.amazon.com/Comimark-XPT8871-Digital-Amplifier-Channel/dp/B07XY5V7K1) | 5–15 zł |
| 2 | **Drut na pętlę** | drut nawojowy emaliowany **0,3 mm** (Cu), 20–40 m | 1 | Allegro: „drut nawojowy 0,3 DNE"; [eBay 0,3 mm](https://www.ebay.com/itm/113961963702); [ICStation 0,3 mm×40 m](https://www.icstation.com/enameled-copper-wire-03mm40m-magnet-winding-wire-transformer-insulated-copper-coil-withstand-voltage-3000-5000v-p-16024.html) | 10–20 zł |
| 3 | **Magnes do ucha** | magnes neodymowy **~2–3 mm** (walec/kulka, powlekany) | kpl | Allegro: „magnes neodymowy 2 mm", „3×1,5 mm" | 5–15 zł |
| 4 | **Wyciągacz** | mocniejszy magnes neodymowy na patyczku / chwytak magnetyczny | 1 | Allegro: „chwytak magnetyczny", „magnes neodymowy walec 8×10" | 5–15 zł |
| 5 | **(Opcja: głośniej)** | gotowa indukcyjna słuchawka **„nano"** (cewka + membrana) | 1 | Allegro/[eBay „nano inductive earpiece"](https://www.ebay.com/itm/186964384770); [Mixspy zestaw](https://mixspy.com/index.php/product/invisible-magnetic-earpieces-full-set-with-neckloop/) | 30–80 zł |
| 6 | **Wtyk do telefonu** | wtyk/pigtail jack **3,5 mm 4‑pin (TRRS)** lub stary kabel od zestawu słuchawkowego | 1 | Allegro: „wtyk jack 3,5 4 pin" | 3–10 zł |
| 7 | **Mikrofon** | moduł mikrofonu **elektretowego** (headset, plug‑in‑power) lub kapsuła + R + C | 1 | AliExpress/Allegro: „mikrofon elektretowy moduł" | 3–10 zł |
| 8 | **Powerbank** | ~1000 mAh, najlepiej z trybem **„always‑on"** + kabel USB do rozcięcia (5 V/GND) | 1 | masz / Allegro | — |
| 9 | **Keep‑alive** | gotowy USB KeepAlive lub elementy na 555 / rezystor 50–150 Ω 1 W | 1 | [Pi Hut KeepAlive](https://thepihut.com/products/power-bank-keepalive-adjustable); [Adafruit poradnik](https://blog.adafruit.com/2020/03/09/keeping-smart-power-banks-alive-while-drawing-low-currents/) | ~20 zł |
| 10 | **Rezystory** | 2× **1 kΩ** (sumowanie L+R) + 1× **2,2–4,7 Ω / 3–5 W** (balast pętli) + ew. 150 Ω (keep‑alive) | kpl | zestaw rezystorów | ~10 zł |
| 11 | **Kondensator** | **1–10 µF** ceramiczny (odsprzęganie VCC) | 1–2 | zestaw | ~5 zł |
| 12 | **Wykończenie** | koszulki termokurczliwe, cienka rurka, klej na gorąco, mała obudowa | kpl | — | ~10 zł |
| 13 | **Narzędzia** | lutownica + cyna + topnik, **multimetr** | — | warsztat | — |

**Łącznie (bez narzędzi): ~60–120 zł** (goły magnes) / **+30–80 zł** za słuchawkę cewkową „nano".

### 2.1. Gdzie kupić — konkretne linki

Przy każdej pozycji **link‑wyszukiwanie na Allegro** (zawsze aktualne — wybierasz świeżą ofertę) **+ przykład zagraniczny**.

> 💡 **Skrót:** część douszną najlepiej kup **gotową jako zestaw „nano" (pętla + słuchawka + magnes‑wyciągacz)** — goły magnes jest cichy i trudniej go bezpiecznie wyjąć. Resztę (zasilanie, ew. mikrofon) dorabiasz sam.

| Część | Co wybrać | Linki |
|---|---|---|
| **Wzmacniacz** | XPT8871 „OEP 5W" | [Allegro: XPT8871](https://allegro.pl/listing?string=XPT8871) · [eBay](https://www.ebay.com/itm/335509230008) · [Banggood 5‑pak](https://usa.banggood.com/5Pcs-XPT8871-5V-5W-1A-Single-Channel-Mono-Digital-Audio-Amplifier-Receiver-Module-Board-p-1268827.html) |
| **⭐ Zestaw nano** (pętla+słuchawka+wyciągacz) | gotowy zestaw indukcyjny, wtyk 3,5 mm | [Allegro: słuchawka indukcyjna nano pętla](https://allegro.pl/listing?string=s%C5%82uchawka%20indukcyjna%20nano%20p%C4%99tla) · [eBay neckloop+nano](https://www.ebay.com/itm/186964384770) · [Amazon zestaw](https://www.amazon.com/Wireless-Invisible-Earpiece-Inductive-Conversation/dp/B092Q33VWY) |
| **Magnes 2–3 mm** (DIY) | walec/dysk N50–N52 ~2×3 mm | [Allegro: magnes neodymowy 2mm](https://allegro.pl/listing?string=magnes%20neodymowy%202mm) · [eBay 3×2 mm](https://www.ebay.com/itm/312045367151) · [SuperMagnetMan 2×3](https://supermagnetman.com/products/d1006b) |
| **Magnes‑wyciągacz** | mocny walec / chwytak teleskopowy | [Allegro: chwytak magnetyczny teleskopowy](https://allegro.pl/listing?string=chwytak%20magnetyczny%20teleskopowy) · [Allegro: magnes neodymowy walec](https://allegro.pl/listing?string=magnes%20neodymowy%20walec) |
| **Drut na pętlę** | nawojowy emaliowany 0,3 mm, 20–40 m | [Allegro: drut nawojowy 0,3mm](https://allegro.pl/listing?string=drut%20nawojowy%200%2C3mm) · [ICStation 0,3 mm×40 m](https://www.icstation.com/enameled-copper-wire-03mm40m-magnet-winding-wire-transformer-insulated-copper-coil-withstand-voltage-3000-5000v-p-16024.html) · [eBay](https://www.ebay.com/itm/113961963702) |
| **Wtyk do telefonu** | jack 3,5 mm 4‑pin TRRS do lutowania (lub stary kabel = darmo) | [Allegro: wtyk jack 3,5 4 pin](https://allegro.pl/listing?string=wtyk%20jack%203%2C5%204%20pin) · [Amazon CESS 2‑pak](https://www.amazon.com/CESS-Black-3-5mm-Headphone-Connector/dp/B01M7Q9OKE) · [eBay 4‑pak](https://www.ebay.com/itm/352581731196) |
| **Mikrofon** | kapsuła elektretowa (zasila telefon) lub moduł | [Allegro: mikrofon elektretowy kapsuła](https://allegro.pl/listing?string=mikrofon%20elektretowy%20kapsu%C5%82a) · [AliExpress moduł](https://www.aliexpress.com/w/wholesale-electret-microphone-module.html) |
| **Powerbank** | mały z trybem „always‑on" (np. INIU) | [Allegro: powerbank always on](https://allegro.pl/listing?string=powerbank%20always%20on) · [Voltaic always‑on](https://voltaicsystems.com/always-on-batteries/) |
| **Keep‑alive** | gotowy USB KeepAlive (jeśli powerbank się wyłącza) | [Pi Hut KeepAlive](https://thepihut.com/products/power-bank-keepalive-adjustable) |
| **Rezystory** | zestaw + osobno **2,2–4,7 Ω / 5 W** (balast) | [Allegro: zestaw rezystorów](https://allegro.pl/listing?string=zestaw%20rezystor%C3%B3w) · [Allegro: rezystor 4,7 om 5W](https://allegro.pl/listing?string=rezystor%204%2C7%20om%205W) |
| **Kondensator** | 1–10 µF | [Allegro: kondensator 10uF](https://allegro.pl/listing?string=kondensator%2010uF) |
| **Drobnica** | koszulki termokurczliwe, klej na gorąco | [Allegro: koszulki termokurczliwe](https://allegro.pl/listing?string=koszulki%20termokurczliwe) |

**Koszyk minimum (najmniej kombinowania):** gotowy **zestaw nano** (ucho+pętla+wyciągacz) + **powerbank** (masz) + ew. **keep‑alive** + **kapsuła elektretowa** (jeśli chcesz, żeby Cię słyszeli). Wtedy **XPT8871 i drut są opcjonalne** — gotowa pętla ma już wzmacniacz w środku. Pełne DIY od zera (własna pętla + XPT8871) ma sens, gdy chcesz to mieć „swoje" i taniej przy większej liczbie sztuk.

---

## 3. Schemat połączeń

```
TELEFON (jack TRRS, std. CTIA)      WZMACNIACZ XPT8871 / OEP SHY-10282        PĘTLA + UCHO
  Tip   (L) ──[ 1kΩ ]──┐
  Ring1 (R) ──[ 1kΩ ]──┴──────────────► IN+
  Ring2 (GND) ──────────┬─────────────► GND ◄─── USB GND (powerbank 5V)
                        │               VCC ◄─── USB +5V ──┬─[ 1–10µF ]─ GND
                        │                                  (kondensator przy VCC)
  Sleeve(MIC) ◄─ mic(+) │               CS ───► do VCC  (włącza wzmacniacz)
   ┌───────────────┐    │               AB ───► do GND  (Klasa AB = czyściej)
   │ moduł elektret│    │               SP+ ─[ 2,2–4,7Ω / 3–5W ]─► koniec pętli A
   └──── mic(-) ────────┘               SP- ─────────────────────► koniec pętli B
                                                         │
                                          PĘTLA: ~3–6 zwojów drutu 0,3 mm na szyję
                                                         │
                                          → pole magnetyczne → MAGNES w uchu drga = DŹWIĘK
```

**Złota zasada:** masa **wspólna** dla wszystkiego (telefon GND = wzmacniacz GND = mikrofon GND).
Brak wspólnej masy = brum albo cisza.

---

## 4. Płytka wzmacniacza (XPT8871 / OEP SHY‑10282)

Płytka z nadrukiem `OEP / SHY‑10282` to moduł z układem **XPT8871** (równoważniki: TC8871, 8871) —
mono wzmacniacz mostkowy (BTL), klasa AB/D do wyboru, zasilanie 3–5 V, do 5 W na 2 Ω.

> **Skąd wiadomo, że to XPT8871? (uczciwie)** Nazwa „XPT8871" **nie jest odczytana z samej kości** —
> układ SOIC‑8 na tych modułach ma zwykle nieczytelny lub ogólny nadruk. Identyfikacja wynika z
> **nadruków na płytce**: `OEP`, `SHY‑10282` oraz linii parametrów `DC 3‑5V`, `5W@2Ω`, `3W@4Ω`. To
> dokładnie „odcisk palca" rodziny **8871** — datasheet XPT8871 podaje te same wartości, a marking
> `5W@2Ω` wyklucza częsty, słabszy **HXJ8002** (tylko 3 W). **Pewność, że to wzmacniacz mono 5 V z
> rodziny 8871: ~95%.** Czy *dokładnie* XPT8871, czy bliźniaczy TC8871/„8871" — **nie ma znaczenia**:
> są pinowo zgodne i lutuje się je identycznie. Realnym ryzykiem nie jest nazwa kości, lecz
> **kolejność padów na Twojej rewizji płytki** → zawsze **przedzwoń piny multimetrem** (niżej), bo
> sitodruki bywają kopiowane między układami i mylą.

**Piny (kieruj się opisem na płytce, nie numerami nóżek IC — bywają różne):**

| Pad | Funkcja | Jak podłączyć |
|---|---|---|
| `VCC` | zasilanie 3–5 V (max 5,5 V) | +5 V z powerbanku |
| `GND` | masa | masa wspólna (USB GND + audio GND) |
| `IN+` | wejście audio (sprzężone kondensatorem na płytce) | sygnał z sumowania L+R |
| `SP+` | wyjście mostek + | przez rezystor balastowy do pętli |
| `SP-` | wyjście mostek − (**aktywne, NIGDY do masy**) | drugi koniec pętli |
| `CS` | włącz/standby — **HIGH = ON** (ma wewn. pull‑down → samo nie wystartuje) | **połącz z VCC**, żeby grał |
| `AB` | wybór klasy: **LOW = Klasa AB** (czyściej), HIGH = Klasa D (wydajniej) | do GND (start od Klasy AB) |

- **Niebieski rezystor na płytce = rezystor wejściowy `Ri` (~20 kΩ)**, ustawia wzmocnienie:
  `Av = 2 × Rf/Ri`, gdzie `Rf ≈ 142 kΩ` (wewnątrz). **Mniejszy Ri = głośniej** (ale uważaj na przester).
  Najpierw zmierz realną wartość Ri na swojej płytce.
- **Przed podaniem zasilania** „przedzwoń" multimetrem piny do nóżek układu i sprawdź, czy nigdzie nie
  ma zwarcia VCC–GND.
- Datasheet/pinout: [components101 XPT8871](https://components101.com/ics/XPT8871-audio-amplifier-ic-pinout-datasheet-circuit);
  zachowanie pinu CS (LOW=off / HIGH=on) potwierdza bliźniaczy moduł:
  [RalphBacon/OEP3W‑MD4103](https://github.com/RalphBacon/OEP3W-MD4103-Amplifier).

---

### 4.1. Alternatywne płytki (byle działało)

Jeśli nie znajdziesz dokładnie tej płytki, zadziała **każdy mały wzmacniacz mono** zasilany 3–5 V,
który uciągnie niską impedancję (2–8 Ω):

| Płytka | Typ | Uwagi | Szukaj |
|---|---|---|---|
| **XPT8871 / TC8871 / „OEP 5W"** | mono BTL, 3–5 V, 5 W | **identyczna z oryginałem (1:1)** — pierwszy wybór | [Allegro](https://allegro.pl/listing?string=XPT8871) |
| **PAM8302 / PAM8302A** | mono klasa D, 2,0–5,5 V, 2,5 W, BTL | najpewniejszy zamiennik; ma pin `SD` (=CS) i `GAIN` | [Allegro](https://allegro.pl/listing?string=PAM8302) |
| **PAM8403** | stereo klasa D, 5 V, 2×3 W, BTL | bardzo tani, wszędzie; **użyj jednego kanału** (L lub R) | [Allegro](https://allegro.pl/listing?string=PAM8403) |
| **HXJ8002 / LM4871 / TDA2822** | mono | starsze, też działają (część single-ended → kondensator na wyjściu) | [Allegro](https://allegro.pl/listing?string=wzmacniacz%20mono%205V) |

**Minimalne wymagania:** wejście audio + masa, zasilanie 3–5 V (USB/powerbank), wyjście głośnikowe
uciągające 2–8 Ω (najlepiej mostkowe/BTL). Podłączenie jak w schemacie: audio→IN, +5 V→VCC, masa
wspólna, wyjście→(balast)→pętla.

> Mapowanie pinów bywa inne na każdej płytce (np. PAM8302: `A+/A-` wejście, `SD`, `GAIN`, `VO+/VO-`).
> Zasada ta sama: wejście z sumowania L+R, włącz `SD/CS`, wyjście przez rezystor balastowy do pętli.

## 5. Pętla indukcyjna

To „antena" nadawcza — kilka zwojów drutu na szyję, napędzanych z wyjścia SP+/SP‑.

**Przepis startowy:**
- Drut: **emaliowany Cu 0,3 mm**, **3–6 zwojów**, obwód ~na szyję (średnica ~13–15 cm).
- **Wariant jak w oryginale (ze zdjęć):** zamiast jednego drutu 0,3 mm użyj **cienkiej litzy** —
  wiązki kilku drutów 0,1–0,2 mm splecionych razem. Elastyczniejsza i wygodniejsza na szyję; końce
  skręć, pocynuj i zalej klejem (patrz [`reference/teardown.md`](reference/teardown.md)).
- Wszystkie zwoje **w tym samym kierunku** (przeciwne się znoszą i zabijają pole).
- Pole rośnie z **amperozwojami**: `H = N·I/(2R)` — więcej zwojów *lub* więcej prądu = głośniej;
  mniejsza pętla = silniejsze pole przy uchu. Cel jakościowy (norma aparatów słuchowych
  [IEC 60118‑4](https://www.univoxaudio.co.uk/knowledge-centre-wiki/standards-legislation-and-best-practice/standard-iec-60118-4-2006)):
  ~400 mA/m w paśmie mowy ~100 Hz–5 kHz.

**Dopasowanie do wzmacniacza (ważne!):** goła pętla ma <1 Ω (prawie zwarcie), a XPT8871 lubi 2–4 Ω.
Dlatego wstaw **rezystor balastowy 2,2–4,7 Ω / 3–5 W szeregowo** między SP+ a pętlę. Chroni wzmacniacz
i wyrównuje pasmo (pętla jest indukcyjna, bez tego ginie góra). To **osobny** rezystor mocy — nie ten
niebieski na płytce.

**Wykonanie:**
1. Nawiń zwoje na szablon o obwodzie szyi, zwiąż w wiązkę.
2. **Ściągnij emalię** z obu końców: kropla gorącej cyny na grocie „wypala" lakier, albo delikatnie
   zeskrob papierem ściernym; potem pocynuj. ([Hackaday — soldering magnet wire](https://hackaday.com/2020/03/09/dont-scrape-magnet-wire-do-this-instead/))
3. Połącz: koniec A → rezystor balastowy → SP+; koniec B → SP‑. Zaizoluj każdy styk koszulką.
4. Schowaj pętlę w cienkiej rurce/materiale (wygoda + ochrona emalii). Dodaj **„breakaway"** (słaby
   punkt/rozłączkę), żeby pętla puściła, gdy się o coś zahaczy.

Inspiracje DIY z konkretnymi liczbami: [Instructables „Invisible Earphones"](https://www.instructables.com/Make-Your-Invisible-Earphones/),
[IEEE Spectrum — DIY induction loop](https://spectrum.ieee.org/a-diy-audio-induction-loop-for-the-hard-of-hearing).

---

## 6. Słuchawka douszna (część w uchu)

> **Wybrana ścieżka: goły magnes neodymowy 1:1 jak oryginał** (najtaniej / max DIY). Poniżej jak go
> zrobić i — co najważniejsze — jak **dostroić go na maksymalną głośność**, bo to **najsłabsze ogniwo**
> całego układu.

**Jak to właściwie działa (uczciwie):** to **nie** jest telecoil (cewka) jak w aparacie słuchowym. Goły
magnes w zmiennym polu pętli **drga mechanicznie** (siła zależy od gradientu pola) i przekazuje drgania
na błonę bębenkową — dźwięk jest **cichy**, ale słyszalny tuż przy uchu. Tak właśnie działa komercyjna
„Sprytna Słuchawka". Działa realnie, ale głośność trzeba wywalczyć strojeniem.

**Wykonanie / obsługa:**
- Magnes **~2–3 mm** (N50–N52, powlekany). Ucho czyste z wosku (wosk tłumi i ślizga). Wkładaj
  **płytko i ostrożnie**.
- **Wyjmowanie: mocniejszym magnesem‑„wyciągaczem"** zbliżonym do ucha (przyciąga magnes z kanału).
  Przećwicz to *poza uchem*, zanim cokolwiek włożysz.

**Plan B głośności — gdy za cicho (kolejność od najtańszej):**
1. **Mocniejszy/większy magnes** (N52, ~3 mm), osadzony głębiej/szczelniej — siła rośnie z momentem
   magnesu i gradientem pola (kompromis: trudniej wyjąć).
2. **Więcej prądu w pętli:** zmniejsz rezystor balastowy (4,7 Ω → 2,2 Ω) i/lub dodaj zwojów; pilnuj,
   by wzmacniacz „widział" ≥2 Ω i się nie przegrzewał.
3. **Pętla bliżej ucha:** mniejsza pętla zauszna/na opasce zamiast na szyję — pole bliskie szybko
   spada z odległością, więc bliżej = znacznie głośniej.
4. **Większe wzmocnienie:** mniejszy `Ri` (niebieski rezystor na płytce) — uwaga na przester/szum.
5. **Plan B sprzętowy: gotowa słuchawka cewkowa „nano"** (poz. 5 BOM). Ma mikro‑cewkę + membranę
   (mini głośnik sterowany polem) — **wyraźnie głośniej i czyściej** niż goły magnes. To pewne
   wyjście, gdy 1–4 nie wystarczą; w rozmiarze 2–3 mm nie robi się jej samodzielnie — kupuje się gotową.

---

## 7. Tor audio z telefonu (TRRS)

Wtyk 4‑pin, standard **CTIA** (większość telefonów): **Tip=L, Ring1=R, Ring2=GND, Sleeve=MIC**.
(Starszy **OMTP** ma zamienione MIC↔GND — jeśli mikrofon nie działa, zamień te dwa.)
[Wikipedia — phone connector](https://en.wikipedia.org/wiki/Phone_connector_(audio)).

- **Sumowanie L+R do mono:** Tip i Ring1 każdy przez **1 kΩ** do wspólnego węzła → `IN+`. Nie zwieraj L i R
  bezpośrednio (rezystory izolują wyjścia telefonu).
- **GND** (Ring2) → `GND` płytki (masa wspólna).
- Wejście XPT8871 jest sprzężone kondensatorem na płytce, więc zwykle wystarczy podać sygnał. Jeśli
  jest za głośno/przester — zwiększ Ri lub dodaj mały dzielnik/atenuator na wejściu.

---

## 8. Tor mikrofonu (dwukierunkowo)

Żeby osoba podpowiadająca Cię słyszała przez połączenie:
- Moduł **elektretowy**: wyprowadzenie „gorące" → **Sleeve (MIC)**, masa modułu → **Ring2 (GND)**.
- Telefon **sam zasila** elektret („plug‑in power" — napięcie bias na pinie MIC), więc **nie trzeba
  osobnej baterii** do mikrofonu. Zwykle wystarczy kapsuła + drobny kondensator sprzęgający/rezystor.
- To pasywny moduł (jak zielona płytka w oryginale), nie aktywny przedwzmacniacz.
- Masa mikrofonu = wspólna masa układu.

---

## 9. Zasilanie i keep‑alive

- **5 V z powerbanku** → `VCC`/`GND`. Dodaj **1–10 µF** ceramiczny tuż przy `VCC`/`GND` (odsprzęganie,
  mniej szumu).
- Pobór jest mały i zmienny → **„smart" powerbanki potrafią się wyłączyć** po kilkudziesięciu sekundach.
  Rozwiązania:
  1. Powerbank z trybem **„always‑on" / „low‑current"** (najprościej).
  2. Gotowy **USB KeepAlive** ([Pi Hut](https://thepihut.com/products/power-bank-keepalive-adjustable)) — pulsuje prąd,
     by powerbank nie zasnął.
  3. DIY: układ na **555** pulsujący obciążenie, albo prosto **rezystor ~50–150 Ω 1 W** na 5 V (pobiera
     trochę prądu, by utrzymać powerbank). ([Adafruit](https://blog.adafruit.com/2020/03/09/keeping-smart-power-banks-alive-while-drawing-low-currents/))
- Redukcja brumu: skręć przewody sygnałowe, krótkie połączenia, czysta wspólna masa.

---

## 10. Montaż, wykończenie i ukrycie (jak na zdjęciach)

- **Lutuj czysto**, krótkie połączenia, każdy styk w koszulce termokurczliwej — bez gołych drutów.
- **Zalej/odciąż złącza klejem na gorąco** (jak biały klej na zdjęciach), zwłaszcza przy cienkim drucie
  nawojowym i przy wtyku — to najczęstsze miejsce urwania.
- Moduł schowaj w **małej obudowie/koszulce**; pętlę w cienkiej rurce pod kołnierzem.
- Powerbank w kieszeni; kabel USB i jack poprowadzone dyskretnie.

---

## 11. Uruchomienie i strojenie (kolejność)

1. **Test na sucho:** multimetrem sprawdź brak zwarcia VCC–GND; potwierdź `CS→VCC`, `AB→GND`.
2. **Zasilanie:** podłącz 5 V, sprawdź pobór na linii USB (czy powerbank nie ucina → keep‑alive).
3. **Test pola (bez ucha):** podaj cichą muzykę/mowę z telefonu, zbliż **magnes do pętli** — powinien
   słyszalnie drgać/brzęczeć. To dowód, że łańcuch audio→pętla→pole działa.
4. **Test w uchu:** włóż magnes, ustaw umiarkowaną głośność, dostrój.
5. **Strojenie głośności:** za cicho → więcej zwojów / mniejszy balast / mniejszy Ri; za głośno/przester
   → odwrotnie. Pilnuj, by wzmacniacz i rezystor balastowy się nie przegrzewały.
6. **Test mikrofonu:** zadzwoń próbnie — czy druga strona Cię słyszy (jeśli nie → zamień MIC/GND = OMTP).

---

## 12. Typowe problemy i naprawa

| Objaw | Prawdopodobna przyczyna | Co zrobić |
|---|---|---|
| Za cicho / ledwo słychać | słabe pole, balast za duży, magnes płytko/za słaby | więcej zwojów, mniejszy balast, głębiej/szczelniej, mocniejszy magnes lub słuchawka cewkowa |
| Brum/szum | brak wspólnej masy, zakłócenia sieciowe, brud na zasilaniu | wspólna masa, kondensator przy VCC, z dala od zasilaczy/świetlówek |
| Zniekształcenia/przester | za duże wzmocnienie/sygnał | większy Ri, niższa głośność w telefonie, dzielnik na wejściu |
| Powerbank wyłącza się po chwili | auto‑off przy małym poborze | tryb always‑on / keep‑alive / rezystor podtrzymujący |
| Mikrofon głuchy | norma OMTP vs CTIA, zła masa | zamień MIC↔GND; sprawdź wspólną masę |
| Wzmacniacz grzeje się / cichnie | zbyt niska impedancja (pętla bez balastu) | dodaj/zwiększ rezystor balastowy (≥2–4 Ω) |
| Brak dźwięku w ogóle | `CS` nie podany na HIGH | połącz `CS` z `VCC` |

---

## 13. Warianty

- **(a) 1:1 najtaniej** — opisany wyżej: goły magnes + własna pętla. Najtańszy, cichszy.
- **(b) Głośniej/pewniej** — gotowa słuchawka cewkowa „nano" zamiast magnesu. Największy skok jakości.
- **(c) Bez kabla (Bluetooth)** — zamiast jacka moduł Bluetooth z wbudowaną pętlą; wygodniej, drożej,
  do rozważenia później.

---

## 14. Checklist „co kupić dziś"

- [ ] Płytka **XPT8871 / OEP 5W** (×1–2)
- [ ] **Drut nawojowy 0,3 mm** (rolka)
- [ ] **Magnes neodymowy 2–3 mm** + **mocniejszy magnes‑wyciągacz**
- [ ] (opcja) **słuchawka indukcyjna „nano"**
- [ ] **Wtyk jack 3,5 mm 4‑pin (TRRS)** lub stary kabel od headsetu
- [ ] **Moduł mikrofonu elektretowego**
- [ ] **Powerbank** (always‑on) + **kabel USB**
- [ ] **Rezystory** 2× 1 kΩ, 1× 2,2–4,7 Ω/3–5 W (+ 150 Ω keep‑alive)
- [ ] **Kondensator** 1–10 µF
- [ ] Koszulki, rurka, klej na gorąco, obudowa
- [ ] Lutownica, cyna, topnik, **multimetr**

---

## 15. Źródła

- XPT8871 — datasheet/pinout: <https://components101.com/ics/XPT8871-audio-amplifier-ic-pinout-datasheet-circuit>
- Bliźniaczy moduł (zachowanie CS, wiring): <https://github.com/RalphBacon/OEP3W-MD4103-Amplifier>
- Pętla indukcyjna / fizyka i DIY: <https://en.wikipedia.org/wiki/Audio_induction_loop> · <https://spectrum.ieee.org/a-diy-audio-induction-loop-for-the-hard-of-hearing> · <https://www.instructables.com/Make-Your-Invisible-Earphones/>
- Norma pola pętli (IEC 60118‑4): <https://www.univoxaudio.co.uk/knowledge-centre-wiki/standards-legislation-and-best-practice/standard-iec-60118-4-2006>
- Wtyk TRRS (CTIA/OMTP): <https://en.wikipedia.org/wiki/Phone_connector_(audio)>
- Lutowanie drutu emaliowanego: <https://hackaday.com/2020/03/09/dont-scrape-magnet-wire-do-this-instead/>
- Powerbank keep‑alive: <https://blog.adafruit.com/2020/03/09/keeping-smart-power-banks-alive-while-drawing-low-currents/> · <https://thepihut.com/products/power-bank-keepalive-adjustable>
- Przykłady zakupu XPT8871: <https://usa.banggood.com/5Pcs-XPT8871-5V-5W-1A-Single-Channel-Mono-Digital-Audio-Amplifier-Receiver-Module-Board-p-1268827.html>

---

*Dokument poglądowy do samodzielnej budowy. Dobieraj elementy z głową, testuj na małej głośności i
pamiętaj o bezpieczeństwie ucha (sekcja na górze).*
