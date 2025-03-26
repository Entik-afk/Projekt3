# Projekt: Volební výsledky scraper

## Popis projektu
Tento projekt slouží k získávání volebních výsledků z webových stránek ČSÚ a jejich ukládání do CSV souboru. Program stáhne data o volbách v jednotlivých obcích, zpracuje je a uloží do tabulkového formátu.

## Požadavky
- Python 3.x
- Knihovny:
  - `requests` – pro stahování dat z webu
  - `beautifulsoup4` – pro parsování HTML
  - `csv` – pro práci s CSV soubory

## Instalace
1. Naklonujte repozitář:
   ```sh
   git clone <URL_REPOZITÁŘE>
   cd <NÁZEV_SLOŽKY>
   ```
2. Nainstalujte závislosti:
   ```sh
   pip install -r requirements.txt
   ```

### Doporučené použití virtuálního prostředí
Pro zachování čistoty systémového prostředí doporučujeme použít **virtuální prostředí**:

1. **Vytvoření a aktivace virtuálního prostředí**:
   ```sh
   python -m venv venv
   source venv/bin/activate  # Na Windows: venv\Scripts\activate
   ```

2. **Instalace závislostí**:
   ```sh
   pip install -r requirements.txt
   ```

3. **Spuštění programu**:
   ```sh
   python main.py <URL> <NAZEV_SOUBORU.csv>
   ```

## Použití
Spusťte skript s následující syntaxi:
```sh
python main.py "<URL_VOLEBNÍ_STRÁNKY>" <NAZEV_SOUBORU.csv>
```
Příklad:
```sh
python main.py "https://www.volby.cz/pls/ps2017nss/ps311?xjazyk=CZ&xkraj=12&xobec=590223&xvyber=7103" ukol.csv
```

## Struktura výstupního CSV souboru
CSV soubor obsahuje následující sloupce:
- `code` – Kód obce
- `location` – Název obce
- `registered` – Počet registrovaných voličů
- `envelopes` – Počet vydaných obálek
- `valid` – Počet platných hlasů
- Hlasy pro jednotlivé strany (každá strana má vlastní sloupec)

Ukázka výstupního CSV:
```
code,location,registered,envelopes,valid,Party A,Party B,Party C
590223,Obec 1,1000,900,850,400,300,150
590224,Obec 2,1200,1100,1050,500,400,150
```

## Jak kód funguje
1. **Načtení argumentů** – Program získá URL stránky s volebními výsledky a název CSV souboru.
2. **Stažení a zpracování hlavní stránky** – Program najde seznam obcí a odkazy na jejich volební výsledky.
3. **Stažení dat pro každou obec** – Program získá detailní statistiky o voličích a hlasech pro jednotlivé strany.
4. **Uložení dat do CSV** – Data se zapíšou do souboru ve strukturované podobě.

## Možné chyby a jejich řešení
- **Nesprávný formát URL** – Ujistěte se, že používáte platnou adresu volební stránky ČSÚ.
- **Neúplná data** – Pokud program nenajde tabulky s daty, může být problém se změnou struktury webu.
- **Chyba připojení** – Ověřte, zda máte internetové připojení a zda je web dostupný.

## Výstup
Po úspěšném dokončení běhu programu se zobrazí zpráva:
```
Hotovo! Data byla úspěšně uložena.
```
Tento soubor lze poté otevřít v tabulkovém procesoru, jako je Excel nebo Google Sheets.

## Autor
- **Jméno:** Lech Gajdzica
- **Email:** lech.gajdzica@hotmail.com


