# VIA MOBILE SMS Marketing (Desktop App)

Jednoduchá desktopová aplikácia (vytvorená v JavaFX) určená pre klientov a partnerov [VIA MOBILE](https://viamobile.sk/) (prevádzkovateľa [SMS Marketing](https://smsmarketing.sk/)), ktorá umožňuje pohodlné hromadné odosielanie SMS správ priamo z Excel súboru.

Aplikácia komunikuje s oficiálnym `JSON API` Viamobile a je navrhnutá tak, aby maximálne zjednodušila proces odosielania stoviek alebo tisícok SMS naraz bez potreby integrácie vlastných systémov.

### Ukážky aplikácie

| Hlavné okno (Hromadná SMS) | Personalizované SMS (s náhľadom) |
| :---: | :---: |
| <img src="https://github.com/SmartVibeCodes/VIA-MOBILE/releases/download/VIAMOBILE/screen_tab1.jpg" alt="Ukážka Tab 1" width="100%"> | <img src="https://github.com/SmartVibeCodes/VIA-MOBILE/releases/download/VIAMOBILE/screen_tab2.jpg" alt="Ukážka Tab 2" width="100%"> |
| **Tmavý režim** | **Dialóg nastavení** |
| <img src="https://github.com/SmartVibeCodes/VIA-MOBILE/releases/download/VIAMOBILE/screen_darkmode.jpg" alt="Ukážka Tmavý režim" width="100%"> | <img src="https://github.com/SmartVibeCodes/VIA-MOBILE/releases/download/VIAMOBILE/screen_settings.jpg" alt="Ukážka Nastavenia" width="100%"> |



## Hlavné funkcie

* **Moderné a jednoduché GUI:** Prehľadné rozhranie s dvoma záložkami pre jednoduché použitie.
* **Svetlý a Tmavý režim:** Prepínanie vizuálnej témy pre pohodlie pri práci.
* **Bezpečné uloženie údajov:** Aplikácia si bezpečne uloží vaše API meno a heslo (pomocou Java Preferences).

### Režim 1: Hromadná SMS

* Umožňuje odoslať **jeden spoločný text** tisíckam príjemcov.
* Stačí nahrať Excel súbor, kde je v **Stĺpci A** zoznam telefónnych čísel.
* **Dynamické počítadlo SMS:** Okamžite vidíte, koľko znakov píšete a na koľko SMS častí bude správa rozdelená (podľa GSM vs UTF-8).

### Režim 2: Personalizované SMS

* Umožňuje odoslať **rozdielny text** každému príjemcovi.
* Excel súbor musí obsahovať:
    * **Stĺpec A:** Telefónne čísla
    * **Stĺpec B:** Vlastný text pre dané číslo
* Aplikácia automaticky **preskočí riadky**, kde chýba buď číslo alebo text.

### Kontrola pred odoslaním

* **Náhľad súboru:** Po načítaní Excelu aplikácia okamžite zobrazí **náhľad prvých 10 riadkov** a **celkový počet** načítaných SMS. Používateľ si tak môže byť istý, že má správne formátovaný súbor ešte pred odoslaním.
* **Voľba kódovania:** Používateľ si môže jednoducho zvoliť, či chce odoslať správy s diakritikou (`UTF-8`) alebo bez nej (`GSM` - lacnejšia tarifa).

### Pokročilé spracovanie výsledkov

* **Automatické ukladanie:** Aplikácia sa nepýta, kam súbor uložiť. Výsledky automaticky ukladá na **Plochu (Desktop)** s unikátnym názvom (napr. `vysledky_sms_viamobile_2025-10-26_160000.xlsx`), aby sa predišlo prepísaniu starých dát.
* **Detailný Log Servera:** Do výstupného Excelu sa ukladá podrobný report pre každú SMS:
    * `Log Servera (Prijatie)`: Okamžitý status z API (`ok`, `blacklist`, `error`).
    * `Naše ID (pre Web)`: Unikátne ID (timestamp), ktoré aplikácia vygenerovala. Slúži na párovanie doručeniek vo webovom rozhraní Viamobile.
    * `Server ID (pre Support)`: Interné `bsmsId` vrátené serverom, užitočné pre technickú podporu.

---

## Technológie

* **Java 21**
* **JavaFX** (pre moderné GUI)
* **Maven** (pre správu závislostí a build)
* **Apache POI** (pre prácu s `.xlsx` súbormi)
* **Jackson** (pre spracovanie JSON API)
* **jpackage** (pre vytvorenie finálneho `.exe` inštalátora pre Windows)
