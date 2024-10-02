summary: Cvičenie 2B For-cyklus
id: cvicenie-2b
categories: cvicenie
tags: beginner, with-bonus
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 2B For-cyklus

<!-- ------------------------ -->
## Úvod

Na tomto cvičení sú úlohy, ktoré majú precvičiť programy s opakovaním použitím tzv. for cyklu.

### Obsah
- použitie výrazu for
- práca s prerušením cyklu
- zakomponovanie if-else výrazu a for cyklu

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C. Napríklad stránku [OneCompiler for C](https://onecompiler.com/c)

Riešenia na jednotlivé úlohy budú uverejnené najskôr nasledujúci deň po cvičení.

<!-- ------------------------ -->
## Úloha 2.8

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypíše na obrazovku čísla _od 1 po N_.
Hodnotu _N_ zadaná používateľ cez štandardný vstup.

### Príklady vstupov / výstupov programu

Pre číslo **10** na vstupe program vypíše postupnosť **1 2 3 4 5 6 7 8 9 10**.

<!-- ------------------------ -->
## Úloha 2.9

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypíše na obrazovku prvých _N_ párnych čísiel,
začínajúc dvojkou. Počet čísiel na vypísanie určuje používateľ zo štandardného vstupu.

### Príklady vstupov / výstupov programu

- Pre zadanie **N = 1** vypíše program na obrazovku číslo **2**.
- Pre zadanie **N = 5** vypíše program na obrazovku čísla **2 4 6 8 10**, každé na nový riadok.
- Pre zadanie **N = 10** vypíše program na obrazovku čísla **2 4 6 8 10 12 14 16 18 20**, každé na nový riadok

<!-- ------------------------ -->
## Úloha 2.10

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý pre vstupný parameter _n_ vráti tzv. súčet štvorcov
pomocou vzorca _1^2 + 2^2 + 3^2 + ... + n^2_ pričom tento súčet vypočítajte pomocou for-cyklu. Hodnotu parametru _n_ zadá
používateľ cez štandardný vstup.

### Príklady vstupov / výstupov programu

- Program pre **n = 3** vypíše hodnotu **14**, pretože **14 = 1^2 + 2^2 + 3^2**
- Program pre **n = 5** vypíše hodnotu **55**, pretože **55 = 1^2 + 2^2 + 3^2 + 4^2 + 5^2**

<!-- ------------------------ -->
## Úloha 2.11

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý má 3 vstupné parametre _a0, d a N_, v tomto
poradí. Program vypíše prvých _N_ členov aritmetickej postupnosti, ktorej prvý člen má hodnotu _a0_ a
diferencia postupnosti je daná parametrom _d_. Pri riešení úlohy použite for-cyklus.

> aside positive
> Ak neviete, čo je to aritmetická postupnosť, môžete sa to dočítať napr. tu: [https://sk.wikipedia.org/wiki/Aritmetick%C3%A1_postupnos%C5%A5](https://sk.wikipedia.org/wiki/Aritmetick%C3%A1_postupnos%C5%A5). 
> V skratke, aritmetická postupnosť je postupnosť čísiel, v ktorej je člen postupnosti rovný súčtu 
> predošlého člena postupnosti a diferencie _d_. Ak by _ai_ a _ai+1_ boli 2 po sebe idúce členy postupnosti, 
> potom _ai+1 = ai + d_.

### Príklady vstupov / výstupov programu

Volanie programu s parametrami 1,2,5 vypíše čísla 1 3 5 7 9 (každé na nový riadok).

##### Zdôvodnenie 
Argumenty 1,2,5 predstavujú hodnoty parametrov a0 = 1, d = 2, N = 5.
Teda prvý člen postupnosti je a0 = 1, členy postupnosti sa od seba líšia o diferenciu d = 2 a chceme
vypísať N = 5 členov postupnosti. Teda sa vypíšu čísla:
- 1 (lebo prvý člen postupnosti je a0 = 1)
- 3 (lebo druhý člen postupnosti je prvý člen + diferencia = 1 + 2 = 3)
- 5 (lebo tretí člen postupnosti je druhý člen + diferencia = 3 + 2 = 5)
- 7 (lebo štvrtý člen postupnosti je tretí člen + diferencia = 5 + 2 = 7)
- 9 (lebo piaty člen postupnosti je štvrtý člen + diferencia = 7 + 2 = 9)

Keďže N = 5, vypíšeme len 5 členov postupnosti.

---

Volanie programu s parametrami 5,-3,4 vypíše čísla 5 2 -1 -4 (každé na nový riadok).

##### Zdôvodnenie 
Argumenty 5,-3,4 predstavujú hodnoty parametrov a0 = 5, d = -3, N = 4.
Teda prvý člen postupnosti je a0 = 5, členy postupnosti sa od seba líšia o diferenciu d = -3 a chceme
vypísať N = 4 členov postupnosti. Teda sa vypíšu čísla:
- 5 (lebo prvý člen postupnosti je a0 = 5)
- 2 (lebo druhý člen postupnosti je prvý člen + diferencia = 5 + -3 = 2)
- -1 (lebo tretí člen postupnosti je druhý člen + diferencia = 2 + -3 = -1)
- -4 (lebo štvrtý člen postupnosti je tretí člen + diferencia = -1 + -3 = -4)

Keďže N = 4, vypíšeme len 4 členy postupnosti.

<!-- ------------------------ -->
## Úloha 2.12

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý od používateľa vyžiada hodnotu parameter _n_
a vypíše na obrazovku mriežku s _n riadkami_ a _n stĺpcami_ podľa diagramov nižšie.

Pre **n = 2** (mriežka s 2 „riadkami“ a 2 „stĺpcami“) by mriežka vyzerala nasledovne:
```text
+ - - - - + - - - - +
|         |         |
|         |         |
|         |         |
|         |         |
+ - - - - + - - - - +
|         |         |
|         |         |
|         |         |
|         |         |
+ - - - - + - - - - +
```

Pre **n = 3** (mriežka s 3 „riadkami“ a 3 „stĺpcami“) by mriežka vyzerala nasledovne:
```text
+ - - - - + - - - - + - - - - +
|         |         |         |
|         |         |         |
|         |         |         |
|         |         |         |
+ - - - - + - - - - + - - - - +
|         |         |         |
|         |         |         |
|         |         |         |
|         |         |         |
+ - - - - + - - - - + - - - - +
|         |         |         |
|         |         |         |
|         |         |         |
|         |         |         |
+ - - - - + - - - - + - - - - +
```

> aside positive
> Pre zalomenie reťazca znakov do nového riadku vo funkcii printf môžte použiť znak '\n'.

<!-- ------------------------ -->
## Úloha 2.13

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vyžiada od používateľa cez štandardný vstup
2 parametre _a_ a _b_. Môžete predpokladať, že _a_ aj _b_ sú kladné celé čísla. Funkcia vráti súčin _a*b_. 
Program implementujte bez použitia operátora *, t.j. bez násobenia!

> aside positive
> Zamyslite sa, ako je možné realizovať násobenie len pomocou opakovaného pripočítavania!

### Príklady vstupov / výstupov programu

Spustenie programu s parametrami 2 a 5 vráti hodnotu 10.

<!-- ------------------------ -->
## Úloha 2.14

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý od používateľa vyžiada parameter _n_. 
Môžete predpokladať, že _n_ je kladné celé číslo. Program vypíše postupne na samostatné riadky čísla _od 1 po n_, s krokom +1, 
teda na prvý riadok vypíše 1, na druhý riadok 1 2, na tretí riadok 1 2 3, atď.

### Príklady vstupov / výstupov programu

Spustenie programu s parametrom 5 vypíše:
```text
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

<!-- ------------------------ -->
## ✨ Bonus Úloha 2.15

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý implementuje mocninu.
Používateľ zadá na vstupe dve kladné čísla _n_ a _k_. Program vypíše _k-tu_ mocninu čísla _n_, t.j. _n^k_.
Program implementujte bez použitia operátora * (násobenie) a bez použitia operátora ** (umocnenie).

> aside positive
> Zamyslite sa, ako je možné realizovať násobenie len pomocou opakovaného pripočítavania.

### Príklady vstupov / výstupov programu

- Spustenie programu so vstupnými číslami 1 a 5 vypíše hodnotu 1.
- Spustenie programu so vstupnými číslami 2 a 5 vypíše hodnotu 32.
- Spustenie programu so vstupnými číslami 3 a 4 vypíše hodnotu 81.

<!-- ------------------------ -->
## ✨ Bonus Úloha 2.16

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypíše tabuľku malej násobilky, 
spolu s menami riadkov a stĺpcov pre čísla od 1 po 10. Očakávaný výsledok by mal vyzerať nasledovne:

```text
    1   2   3   4   5   6   7   8   9   10
1   1   2   3   4   5   6   7   8   9   10
2   2   4   6   8   10  12  14  16  18  20
3   3   6   9   12  15  18  21  24  27  30
4   4   8   12  16  20  24  28  32  36  40
5   5   10  15  20  25  30  35  40  45  50
6   6   12  18  24  30  36  42  48  54  60
7   7   14  21  28  35  42  49  56  63  70
8   8   16  24  32  40  48  56  64  72  80
9   9   18  27  36  45  54  63  72  81  90
10  10  20  30  40  50  60  70  80  90  100
```

> aside positive
> Pekné odsadenie textu môžete dostať pomocou ukončovacieho znaku výpisu ‘\t‘ (tabulátor – pre jeho použitie 
> je nutné ho uviesť do úvodzoviek/apostrofov).

