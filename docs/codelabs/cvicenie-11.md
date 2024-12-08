summary: Cvičenie 11 C++ Triedy
id: cvicenie-11
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 11 - C++ Triedy

<!-- ------------------------ -->
## Úvod

Náplňou týchto úloh je ozrejmiť si prácu s C++ jazykom a objektovo-orientovaným prístupom k implementácii programov
pomocou tried.

### Obsah
- definícia triedy v c++
- dedenie
- polymorfizmus

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> g++ -o program -Wall -Wextra main.cpp
> ```

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C++. Napríklad stránku [OneCompiler for C](https://onecompiler.com/cpp)
Avšak odporúčam použiť C++ IDE ako napríklad Clion alebo Visual Studio.

Riešenia na jednotlivé úlohy budú uverejnené neskôr.

<!-- ------------------------ -->
## Úloha 11.1

Napíšte program, zdrojový kód, v jazyku C++ pre správu študentov. Program definuje triedu `Student`, 
ktorá má reprezentovať študenta na škole.
Trieda má obsahovať atribúty (členov):

* Meno (_string_)
* Id (_int_)
* Počet získaných bodov (_float_)

Trieda študenta by mala obsahovať metódy:

* Konštruktor s inicializáciou atribútov
* Metódu na nastavenie a získanie bodov
* Metódu `isPassing`, ktorá vráti true ak študent má viac ako 50 bodov.
* Metódu výpisu informácii o študentovi

### Príklady vstupov / výstupov programu

Program môže obsahovať nasledovnú logiku:

* Vytvorenie študenta: `Student("Alice", 101, 40.5)`
* Nastavenie bodov na _55.0_
* Vypísanie študenta: `Meno: Alice, ID: 101, Body: 55.0, Status: Passing`

<!-- ------------------------ -->
## Úloha 11.2

Napíšte program, zdrojový kód, v jazyku C++, ktorý definuje triedu `Product`, 
ktorá bude reprezentovať produkt v obchode s nasledujúcimi atribútmi:

* Názov produktu (_string_)
* Cena (_float_)
* Počet kusov na sklade (_int_)

Trieda by mala obsahovať metódy:

* Konštruktor na inicializáciu produktu.
* Metódu `sell`, ktorá zníži počet kusov na sklade, ak je dostatok tovaru (inak vypíše chybovú správu).
* Metódu `restock`, ktorá zvýši počet kusov na sklade.
* Metódu na výpis detailov o produkte.

V rámci programu vytvorte pole produktov, následne sa nejaké kusy produktov predajú a zobrazí sa stav skladu.

### Príklady vstupov / výstupov programu

Programm môže obsahovať nasledovnú logiku:

* Vytvorí produkt: `Product("Laptop", 1200.0, 10)`
* Vytvorí produkt: `Product("Stolička", 50.50, 11)`
* Predá 3 kusy laptopov
* Vypíše stav skladu
* Doplní 5 kusov tovaru
* Vypíše stav skladu

<!-- ------------------------ -->
## ⛓️‍💥 Úloha 11.3

Napíšte program, zdrojový kód, v jazyku C++, ktorý implementuje obojstranne zreťazený zoznam pomocou tried.
Každý prvok zoznamu (trieda `ListItem`) by mal obsahovať celé kladné číslo, pointer na ďalší prvok a pointer na predchádzajúci.
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

<!-- ------------------------ -->
## Úloha 11.4

Napíšte program, zdrojový kód, v jazyku C++, ktorý modeluje hierarchiu zamestnancov vo firme pomocou dedičnosti tried. 
Program bude obsahovať tieto triedy:

Základná trieda: `Employee`

**Atribúty**:
* Meno zamestnanca (_string_)
* ID zamestnanca (_int_)

**Metódy**:
* Konštruktor na inicializáciu mena a ID.
* Virtuálna metóda `calculateSalary()`, ktorá vráti základný plat (napr. 1000 EUR).
* Metóda na výpis informácií o zamestnancovi.

Odvodená trieda: `Manager`

Dedí z triedy **Employee**.
**Atribúty**:
* Bonus (_float_)

**Metódy**:
* Preťaženie metódy `calculateSalary()`, ktorá vráti základný plat plus bonus.
* Metóda na nastavenie bonusu.

Odvodená trieda: `Intern`

Dedí z triedy **Employee**.
**Atribúty**:
* Počet hodín praxe (_int_)
* Sadzba za hodinu (_float_)

**Metódy**:
* Preťaženie metódy `calculateSalary()`, ktorá vypočíta plat ako počet hodín * sadzba za hodinu.

V rámci programu:

* Definujte všetky tri triedy a ich príslušné atribúty a metódy.
* Programe vytvorte pole zamestnancov, ktoré bude obsahovať objekty typu _Employee_, _Manager_, a _Intern_.
* Pre každý objekt zavolajte metódu `calculateSalary()` a vypíšte informácie o zamestnancovi vrátane vypočítaného platu.
* Využite princíp dedičnosti a polymorfizmus (virtuálne metódy). Použite dynamickú alokáciu objektov v poli zamestnancov. 
  Dodržujte dobré princípy objektovo-orientovaného návrhu (napr. zapúzdrenie).

### Príklady vstupov / výstupov programu

Program môže obsahovať nasledovné objekty:

* Zamestnanec: Employee("Alice", 1)
* Manažér: Manager("Bob", 2, bonus = 500.0)
* Intern: Intern("Charlie", 3, hodiny = 20, sadzba = 10.0)

```text
Zamestnanec:
Meno: Alice, ID: 1, Plat: 1000.0

Manažér:
Meno: Bob, ID: 2, Plat: 1500.0

Stážista:
Meno: Charlie, ID: 3, Plat: 200.0
```
