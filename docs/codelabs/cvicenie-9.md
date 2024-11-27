summary: Cvičenie 9 Štruktúry
id: cvicenie-9
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 9 - Štruktúry

<!-- ------------------------ -->
## Úvod

Náplňou týchto úloh je precvičiť si prácu so štruktúrami v jazyku C. Úlohy sú definované pre vyskúšanie si štruktúr 
v rôznych prípadoch použitia a práce s nimi.

Pri vypracovaní úloh použite všetky doterajšie znalosti, hlavne z tématiky polí a alokovania pamäte.

### Obsah
- definovanie štruktúry
- inicializácie štruktúry
- práca s členmi štruktúry

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

týchto úloh odporúčam mať funkčné lokálne vývojové prostredie (VS Code, CLion a pod.) a kompilátor jazyka C.

> aside negative
> Nezabudnite každú alokovanú pamäť uvoľniť volaním funkcie `free` ! Je dôležité si po sebe vždy upratať.

Riešenia na jednotlivé úlohy budú uverejnené neskôr.

<!-- ------------------------ -->
## Úloha 9.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu študenta. 
Táto štruktúra by mala obsahovať nasledujúce položky: _meno_ (pole znakov), _vek_ (celé číslo), _priemerný prospech_ (desatinné číslo). 
Program by mal načítať údaje študentov, vypočítať priemerný vek a priemerný prospech všetkých študentov a tieto hodnoty vypísať.

Vstupy programu môžu byť zadané zo štandardného vstupu alebo načítané zo súboru.

### Príklady vstupov / výstupov programu

Pre nasledujúce vstupy programu:

```text
1. Študent
Meno: Ján 
Vek: 20 
Priemerný prospech: 1.5
---
2. Študent
Meno: Petra 
Vek: 22 
Priemerný prospech: 1.8
---
3. Študent
Meno: Milan 
Vek: 19 
Priemerný prospech: 2.0
---
```

Program vypíše na štandardný výstup nasledovný výstup:

```text
Sumár študentov:
Priemerný vek: 20.33 Priemerný prospech: 1.77
```


<!-- ------------------------ -->
## Úloha 9.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu zamestnanca. 
Štruktúra by mala obsahovať _meno_ (pole znakov), _identifikačné číslo_ (celé číslo) a _plat_ (desatinné číslo). 
Program by mal načítať údaje pre niekoľko zamestnancov, zoradiť ich podľa platu zostupne a 
vypísať zoznam zamestnancov spolu s ich platmi. Následne program vypíše priemerný plat zamestnancov.

Údaje o zamestnancoch načítajte zo súboru, kde na jednom riadku je definovaný jeden zamestnanec a hodnoty na riadku sú oddelené medzerou: `ID Meno Plat`

Cestu k súboru načítajte od používateľa zo štandardného vstupu na začiatku programu.

### Príklady vstupov / výstupov programu

Program pre vstupný súbor:

```text
101 Anna 2500.50
102 Peter 3000.75
103 Lucia 2800.00
```

vypíše nasledovný text na výstupe:

```text
102 Peter 3000.75
103 Lucia 2800.00
101 Anna 2500.50
---
Priemerný plat: 2767.08
```

### Bonus

Skúste upraviť výpis tak aby mal formát tabuľky. Nezabudnite na správne zarovnanie stĺpcov. Takýto výstup by mohol vyzerať nasledovne:

```text
|ID  |Meno  |Plat    |
|----|------|--------|
|102 |Peter |3000.75 |
|103 |Lucia |2800.00 |
|101 |Anna  |2500.50 |
---
Priemerný plat: 2767.08
```

<!-- ------------------------ -->
## 🗓️ Úloha 9.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje štruktúru na reprezentáciu dátumu s položkami _deň_, 
_mesiac_ a _rok_ (celé čísla). Program by mal umožniť používateľovi zadať dva dátumy kde jednotlivé hodnoty dátumov sú definované v jednom riadku oddelené medzerou
a vypočítať rozdiel medzi nimi. Rozdieľ je vypísaný ako počet dní medzi dátumami.

V programe ošetrite vstup od používateľa aby bolo možné zadať iba správny dátum (napríklad nie je možné zadať 31.2.) a zohľadňuje priestupné roky.

### Príklady vstupov / výstupov programu

Priebeh programu môže vyzerať nasledovne:

```text
Prvý dátum: 1 1 2023
Druhý dátum: 15 1 2024
---
Rozdiel dátumov: 376 dní
```

```text
Prvý dátum: 28 2 2020
Druhý dátum: 1 3 2020
---
Rozdiel dátumov: 2 dni
```

### Bonus

Skúste upraviť výpis rozdielu dátumov tak aby uviedol pre používateľa rozdiel aj koľko prípadných rokov, mesiacov, či dní je medzi dátumami. Napríklad:

- vstup: 1.1.2023 a 15.1.2024 -> 1 rok a 15 dní
- vstup: 1.1.2022 a 5.3.2022 -> 2 mesiace a 5 dní


<!-- ------------------------ -->
## 📚 Úloha 9.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu knihy v knižnici. 
Štruktúra by mala obsahovať _názov_ (pole znakov), _autora_ (pole znakov) a _rok vydania_ (celé číslo). 
Program by mal načítať údaje zo súboru kde je definovaná kniha na jednom riadku a hodnoty štruktúry sú oddelené bodkočiarkou.
Vstupný súbor môže byť v rovnakom priečinku ako program a môže mať napevno definovaný názov v zdrojovom kóde.
Program po úspešnom spracovaní súboru vypíše počet načítaných kníh.
Program následne umožní zadať používateľovi rok a vypíše knihy, ktoré boli vydané v zadanom roku.

### Príklady vstupov / výstupov programu

Vstupný súbor s knihami

```text
Programovanie v C;Kernighan & Ritchie;1988  
Moderné algoritmy;Jon Bentley;1990  
Umenie programovania;Donald Knuth;1968  
Štruktúra a interpretácia počítačových programov;Harold Abelson & Gerald Jay Sussman;1985  
Cvičenia z programovania;Brian Kernighan;1988  
Algoritmy v C++;Robert Sedgewick;1990  
Čistý kód;Robert C. Martin;2008  
Pragmatický programátor;Andrew Hunt & David Thomas;1999  
Python pre začiatočníkov;Guido van Rossum;2000  
Počítačová grafika;John F. Hughes & James D. Foley;1995  
```

Priebeh programu môže byť nasledovný:

```text
Počet kníh v databáze: 10
Zadajte rok vydania kníh: 1990

Názov: Moderné algoritmy
Autor: Jon Bentley
Rok vydania: 1990
---
Názov: Algoritmy v C++
Autor: Robert Sedgewick
Rok vydania: 1990
```

<!-- ------------------------ -->
## ⛓️‍💥 Úloha 9.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý implementuje jednoduchý zreťazený zoznam pomocou štruktúr. 
Každý prvok zoznamu by mal obsahovať celé kladné číslo a pointer na ďalší prvok.
Program umožní používateľovi cez štandardný vstup zadať číslo prvku zoznamu. Po zadaní vstupu je nový prvok pridaný na koniec zoznamu
a následne vypíše celý aktuálny zoznam a znova ponúkne používateľovi zadať ďalší prvok.
Program končí ak používateľ na vstupe zadá hodnotu -1.

> aside negative
> Nezabudnite uvoľniť pamäť alokovanú pre jednotlivé prvky zoznamu na konci programu!

### Príklady vstupov / výstupov programu

Priebeh programu môže vyzerať nasledovne:

```text
---
Zadajte hodnotu prvku: 1
Aktuálny zoznam: 1
---
Zadajte hodnotu prvku: 85
Aktuálny zoznam: 1, 85
---
Zadajte hodnotu prvku: 423
Aktuálny zoznam: 1, 85, 423
---
Zadajte hodnotu prvku: -1
```
