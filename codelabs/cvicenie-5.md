summary: Cvičenie 5 Súbory
id: cvicenie-5
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 5 - Súbory

<!-- ------------------------ -->
## Úvod

Na tomto cvičení si preberieme prácu so súbormi.

### Obsah
- otvorenie súboru a jeho čítanie
- zapisovanie do súboru

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh odporúčam lokálne vývojové prostredie (napr. CLion alebo VS Code) a nie webové prostredie.

Riešenia na jednotlivé úlohy budú uverejnené najskôr nasledujúci deň po cvičení.

<!-- ------------------------ -->
## Úloha 5.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý otvorí existujúci súbor **_data.txt_**, 
načíta všetky údaje a vypíše ich na štandardný výstup.

Dáta zo súboru načítajte po riadkoch a každý riadok hneď po načítaní vypíšte. Snažte sa implementáciu spraviť tak aby 
v jednom momente bol načítaný len jeden riadok.

> aside positive
> Nezabudnite si pred spustením program vytvoriť súbor _data.txt_ v tom istom priečinku ako zdrojový súbor _main.c_ .

### Obsah súboru _data.txt_

```text
Na prvé cvičenie prišli všetci.
Na druhé už o niečo menej.
Na tretie už o málo menej.
Na štvrté prišli tí, ktorí sa chcú niečo naučiť. 
```

<!-- ------------------------ -->
## Úloha 5.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý zapíše do súboru výpočty, ktoré zadá používateľ.
Program bude sčítavať dve čísla, ktoré zadá používateľ a vypíše ich výsledok na štandardný výstup a zároveň zapíše výpočet do súboru.
Program si pýta dve čísla pre výpočet v cykle do nekonečna pokiaľ používateľ namiesto prvého čísla nezadá znak _'q'_.

Výpočet je uložený do súboru ako trojica čísel oddelená medzerou. Každý výpočet je uložený do nového riadku. 
Výpočty ukladajte do súboru _**vypocty.txt**_ do rovnakého priečinku ako je váš zdrojový súbor _main.c_ .
Ak súbor neexistuje, vytvorte ho programom. Ak súbor pri otvorení existuje prepíšte jeho existujúce dáta novými.

> aside negative
> Dávajte si pozor na zatvorenie súboru pred skončením programu.

### Príklady vstupov / výstupov programu

Ak vstupy od používateľa pre výpočty boli v nasledovnom poradí:

- 5 a 3
- 8 a 7
- 21 a 56

Program by mal vytvoriť súbor _vypocty.txt_ s nasledovným obsahom:

```text
5 3 8
8 7 15
21 56 77
```

<!-- ------------------------ -->
## Úloha 5.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý načíta súbor _vypocty.txt_ a pokračuje v jeho zapisovaní.

Program na začiatku načíta súbor _vypocty.txt_. Ak súbor neexistuje vytvorí ho. Ak súbor existuje načíta postupne z neho všetky výpočty
a zvaliduje či sú správne vypočítané, t.j. či z načítanej trojice čísel v riadku súčet prvých dvoch čísiel sa rovná tretiemu číslu.
Ak kontrola narazí na nesprávny výpočet tak na to upozorní používateľa vypísaním načítaných čísel a chybovou správou,
program však pokračuje ďalej. Keď program načíta všetky existujúce výpočty vypíše koľko výpočtov načítal na obrazovku.

Program následne pokračuje v rovnakej činnosti ako v úlohe 5.2 s opýtaním sa používateľa o dve čísla a vypočíta ich súčet.
Výpočet potom zapíše na koniec súboru. Existujúce dáta nesmú byť prepísané. Formát súboru _vypocty.txt_ musí byť zachovaný
ako je v úlohe 5.2.

> aside negative
> Dávajte si pozor na mód pod ktorým otvárate súbor a na zatvorenie súboru pred skončením programu.
