summary: Cvičenie 1
id: cvicenie-1
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-zpr-2024-codelabs/issues

# Cvičenie 1
<!-- ------------------------ -->
## Úvod

Na prvom cvičení je cieľom sa oboznámiť s programovacím jazykom, vývojovým prostredím 
a rozmýšľaním ako vyriešiť predložený problém ako programátor 😉

### Obsah
- práca s výpisom do terminálu
- práca s premennými
- použitie základných aritmetických operácií
- načítanie vstupu používateľa

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

<!-- ------------------------ -->
## Úloha 1.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Program obsahuje premennú _strana_a_. Do tejto premennej sa priamo v zdrojovom kóde priradí
nejaká hodnota predstavujúca veľkosť strany štvorca. Program najprv vypíše obvod a potom obsah
daného štvorca.

### Príklady vstupov / výstupov programu

Ak sa do premennej _strana_a_ priradí hodnota 5, potom obvod takého štvorca je 20 a obsah takého
štvorca je 25. Program by teda pre situáciu, že v premennej a je uložená hodnota 5, mal vypísať na
obrazovku čísla 20 a 25.

<!-- ------------------------ -->
## Úloha 1.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Program obsahuje premenné _strana_a_ a _strana_b_. Do týchto premenných sa priamo v zdrojovom
kóde priradia nejaké číselné hodnoty predstavujúce veľkosti hrán obdĺžnika. Program najprv vypíše
obvod a potom obsah daného obdĺžnika.

### Príklady vstupov / výstupov programu

Ak sa do premenných _strana_a_ a _strana_b_ priradia hodnoty _strana_a = 3_, _strana_b = 8_, potom
obvod takého obdĺžnika je 22 a obsah takého obdĺžnika je 24. Program teda vypíše hodnoty 22 a 24
na obrazovku.

<!-- ------------------------ -->
## Úloha 1.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Program obsahuje premennú sekundy. Do tejto premennej sa priamo v zdrojovom kóde priradí
číselná hodnota predstavujúca ubehnutý čas v sekundách. Program vypíše, koľko hodín / minút /
sekúnd predstavuje hodnota v premennej sekundy.

### Príklady vstupov / výstupov programu

1) Ak je v premennej sekundy hodnota 5043, program vypíše:
```shell
   1
   24
   3
```
   pretože 5043 sekúnd predstavuje 1 hodinu, 24 minút a 3 sekundy.
2) Ak je v premennej sekundy hodnota 3012, program vypíše:
```shell
   0
   50
   12
```
   pretože 3012 sekúnd predstavuje 0 hodín, 50 minút a 12 sekúnd.
3) Ak je v premennej sekundy hodnota 10000, program vypíše:
```shell
   2
   46
   40
```
   pretože 10000 sekúnd predstavuje 2 hodiny, 46 minút a 40 sekúnd.

> aside positive
> Zvyšok po delení sa dá zistiť pomocou operátora %, t.j. napr. výraz 110 % 4
má hodnotu 2, pretože 110 po delení 4 má zvyšok 2.

### Bonus na precvičenie

Skús zapojiť trochu tvorivosti a naformátujte výstup používateľovi v rôznych podobách. Rôzne špecifikácii formátu môžte nájsť v [tejto dokumentácii](https://cplusplus.com/reference/cstdio/printf/).

<!-- ------------------------ -->
## Úloha 1.4

Cyklista si sleduje prejdenú vzdialenosť v kilometroch a čas (v minútach a sekundách), za ktorý
túto vzdialenosť prešiel. Naprogramujte program, ktorý na základe premenných kilometre, minuty,
sekundy vypočíta cyklistovu priemernú rýchlosť v km/h (kilometre za hodinu) a vypíše ju na
obrazovku. Hodnoty premenných vyžiadajte od používateľa po spustení programu.

### Príklady vstupov / výstupov programu

Napríklad ak kilometre = 8.5, minuty = 25 a sekundy = 30, potom priemerná rýchlosť cyklistu bola
20.0 km/h.

Ak kilometre = 9.7, minuty = 29 a sekundy = 55, potom priemerná rýchlosť cyklistu bola približne
19.454 km/h. 

