# Election Scraper

## Popis projektu
Tento projekt je jednoduchý scraper pro získání volebních výsledků z webu volby.cz. Program zpracovává data o volbách, včetně počtu voličů, vydaných obálek, platných hlasů a výsledků jednotlivých stran pro každou obec.

## Použití
Spuštění programu probíhá pomocí příkazového řádku s následující syntaxí:

```
python projekt_3.py "<odkaz_na_web>" <nazev_souboru.csv>
```

Například:
```
python projekt_3.py "https://www.volby.cz/pls/ps2017nss/ps32?xjazyk=CZ&xkraj=12&xnumnuts=7103" "vysledky.csv"
```

## Instalace a závislosti
Před spuštěním skriptu se ujistěte, že máte nainstalované všechny potřebné knihovny. Ty lze nainstalovat pomocí příkazu:
```
pip install -r requirements.txt
```

Seznam požadovaných knihoven:
- `requests` - pro stahování webových stránek
- `beautifulsoup4` - pro parsování HTML
- `csv` - pro práci se soubory CSV

## Popis funkcí

### `ziskat_argumenty() -> Tuple[str, str]`
Získá argumenty z příkazového řádku – odkaz na volební stránku a název výstupního CSV souboru.

### `parsovani_odkazu(odkaz: str) -> BeautifulSoup`
Načte HTML stránku a vrátí ji jako objekt BeautifulSoup.

### `najdi_odkaz_obec(soup: BeautifulSoup) -> Tuple[List[str], List[str]]`
Najde kódy a názvy všech obcí v zadané oblasti a vrátí je ve formě seznamů.

### `ziskat_data_obce(odkaz: str) -> Tuple[str, str, str, List[Tuple[str, str]]]`
Stáhne volební výsledky pro konkrétní obec, včetně počtu voličů, vydaných obálek, platných hlasů a hlasů pro jednotlivé strany.

### `main() -> None`
Hlavní funkce programu, která řídí celý proces:
1. Načte argumenty z příkazového řádku.
2. Stáhne seznam obcí.
3. Pro každou obec získá podrobné volební výsledky.
4. Uloží výsledky do CSV souboru.

## Výstupní soubor
Výstupní CSV soubor bude obsahovat následující sloupce:
- `code` – kód obce
- `location` – název obce
- `registered` – počet registrovaných voličů
- `envelopes` – počet vydaných obálek
- `valid` – počet platných hlasů
- a jednotlivé strany s jejich počtem hlasů

## Autor
- **Jméno:** Lech Gajdzica
- **Email:** lech.gajdzica@hotmail.com


