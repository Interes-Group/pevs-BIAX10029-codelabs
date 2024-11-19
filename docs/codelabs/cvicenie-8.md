summary: Cvičenie 8 Dynamic Allocation
id: cvicenie-8
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 8 - Dynamická alokácia pamäte

<!-- ------------------------ -->
## Úvod

Náplňou tohto cvičenie je oboznámiť sa s dynamickou alokáciou pamäte a práce s pointrami.

Pri vypracovaní cvičení si je potrebné uvedomiť s akými typmi a akú veľkosť pamäte si program alokuje.

### Obsah
- alokácia dynamického pola
- realokácia existujúceho bloku pamäte


> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh odporúčam mať funkčné lokálne vývojové prostredie (VS Code, CLion a pod.) a kompilátor jazyka C.

> aside negative
> Nezabudnite každú alokovanú pamäť uvoľniť volaním funkcie `free` ! Je dôležité si po sebe vždy upratať. 

Riešenia na jednotlivé úlohy budú uverejnené neskôr.

<!-- ------------------------ -->
## Úloha 8.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypýta na vstupe od používateľa číslo `int n`
a následne alokuje pamäť _n_ blokov každý o veľkosti typu _int_.

Po alokácií program vypíše jednotlivé hodnoty čísle v alokovanej pamäti.


<!-- ------------------------ -->
## Úloha 8.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý nadväzuje na úlohu 8.1. Do alokovanej pamäte zapíšte
čísla od 1 do _n_.

Následne program vypíše na štandardný výstup adresu alokovanej pamäte a zároveň jednotlivé zapísané hodnoty aj s ich adresou.

### Príklady vstupov / výstupov programu

Pre vstup 3 bude výpis vyzerať nasledovne:

```text
Adresa alokovanej pamäte: 0x0000475d21a
0. položka: adresa = 0x0000475d21a ; hodnota = 1
1. položka: adresa = 0x0000475d21b ; hodnota = 2
2. položka: adresa = 0x0000475d21c ; hodnota = 3
```

<!-- ------------------------ -->
## Úloha 8.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý nadväzuje na úlohu 8.1. Do alokovanej program
postupne vyžiada od používateľa jednotlivé čísla ako prvky dynamického poľa.

Následne program vypíše na štandardný výstup adresu alokovanej pamäte a zároveň jednotlivé zapísané hodnoty aj s ich adresou.

### Príklady vstupov / výstupov programu

Priebeh programu môže byť nasledovný:

```text
Zadajte počet prvkov: 3
Zadanie 1. prvok: 85
Zadanie 2. prvok: 41
Zadanie 3. prvok: -2
Adresa alokovanej pamäte: 0x000784b111
0. položka: adresa = 0x000784b111 ; hodnota = 85
1. položka: adresa = 0x000784b112 ; hodnota = 41
2. položka: adresa = 0x000784b113 ; hodnota = -2
```


<!-- ------------------------ -->
## Úloha 8.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý načíta od používateľa počet slov `int n` (_n_ je zadané od používateľa)
a ich maximálnu dĺžku `int maxLen`. Následne program dynamicky alokuje pole reťazcov. Pre každé slovo alokuje novú dynamickú pamäť pre samotný reťazec
ako prvok poľa. Slovo má maximálne dĺžku definovanú používateľom.

Program postupne od používateľa načíta _n_ slov. Po načítaní všetkách slov vypíše načítané slová a ich dĺžky.

> aside positive
> Pre získanie dĺžky reťazcov je možné použiť funkciu `strlen` z knižnice `&lt;string.h>`

### Príklady vstupov / výstupov programu

Priebeh programu môže byť nasledovný:

```text
Zadajte počet slov: 3
Zadajte maximálnu dĺžku slova: 10
Zadajte slová:
ahoj
programovanie
C
---
Slová a ich dĺžky:
ahoj (4 znaky)
programovanie (13 znakov)
C (1 znak)
```


<!-- ------------------------ -->
## Úloha 8.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý na začiatku alokuje pamäť o veľkosti 5 čísel 
(t.j. pole veľkosti `5*sizeof(int)`). Následne umožní používateľovi pridávať hodnoty to poľa zo štandardného vstupu.
Ak sa pole naplní, zmeňte jeho alokovanú veľkosť na dvojnásobnú aktuálnej veľkosti a umožnite používateľa ďalej zadávať čísla.
Pokračujte načítanie hodnôt pokým používateľ nezadá hodnotu **-1**, ktorý ukonči zadávanie čísel.

Na záver, program vypíše všetky načítané čísla, veľkosť a adresu alokovanej pamäte.

Nezabudnite patrične uvoľniť alokovanú pamäť a ošetriť prípady keď alokácia pamäte zlyhá.

### Príklady vstupov / výstupov programu

Priebeh programu môže byť nasledovný:

```text
Zadajte hodnoty (zadaním -1 ukončíte): 
10
20
30
40
50
60
70
-1
---
Zadané hodnoty: 10 20 30 40 50 60 70
Konečná veľkosť poľa: 10 prvkov
Adresa poľa: 0x000044781dcc
```


<!-- ------------------------ -->
## Úloha 8.6

Majme nasledujúci program:

```C
void runMe(){
    int* leakingPtr = (int*) malloc(sizeof(int)*1024);
    for(int i=0;i<1024;i++){
        leakingPtr[i] = i+1000;
    }
}

int main(){
    runMe();
    return 0;
}
```

1. Ako vyzerá alokovaná pamäť program pred a po volaní funkcie `runMe`?
2. Čo je zlé s funkciou `runMe`? (minimálne 2 veci)
3. Prepíšte program tak aby bol korektný.
