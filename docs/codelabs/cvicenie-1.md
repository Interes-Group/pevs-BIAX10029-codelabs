summary: Cvičenie 1
id: cvicenie-1
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

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

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C. Napríklad stránku [OneCompiler for C](https://onecompiler.com/c)

Riešenia na jednotlivé úlohy budú uverejnené nasledujúci deň po cvičení.

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

### Riešenie

```C
#include <stdio.h>

int main()
{
    int strana_a = 5;
    
    printf("Veľkosť strany štvorca: %d\n",strana_a);
    printf("Obvod štvorca: %d\n", 4*strana_a);
    printf("Obsah štvorca: %d\n", strana_a * strana_a);
    return 0;
}
```

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

### Riešenie

```C
#include <stdio.h>

int main()
{
    int strana_a = 3;
    int strana_b = 8;
    
    printf("Strany obdĺžníka: a=%d, b=%d\n",strana_a, strana_b);
    printf("Obvod obdĺžníka: %d\n", 2*strana_a + 2*strana_b);
    printf("Obsah obdĺžníka: %d\n", strana_a * strana_b);
    return 0;
}
```

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

### Riešenie

```C
#include <stdio.h>

int main()
{
    int sekundy = 10000;
    
    int hodiny, minuty, zvysne_sekundy;
    
    hodiny = sekundy / 3600;
    minuty = (sekundy % 3600) / 60;
    zvysne_sekundy = sekundy % 60;
    
    printf("Vstupný počet sekúnd: %d\n",sekundy);
    printf("hodiny: %d\n",hodiny);
    printf("minúty: %d\n", minuty);
    printf("sekundy: %d\n", zvysne_sekundy);
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 1.4

Napíšte program, ktorý prehodí hodnoty medzi dvomi premennými a vypíše ich. 
Premenné sú typu **int** a ich hodnota je zadaná používateľov po spustení programu.

### Príklady vstupov / výstupov programu

Ak používateľ zadaná hodnotu prvej premennej _5_ a druhej premennej _8_, po zadaní druhej premennej je vypísaný výstup
po prehodení hodnôte, teda prvá premenná bude mať hodnotu _8_ a druhá premenná hodnotu _5_.

### Riešenie

```C
#include <stdio.h>

int main()
{
    int prva;
    int druha;
    
    printf("Zadajte prvú hodnotu: ");
    scanf("%d",&prva);
    
    printf("Zadajte druhú hodnotu: ");
    scanf("%d",&druha);
    
    int odlozena = prva;
    prva = druha;
    druha = odlozena;
    
    printf("Prehodené hodnoty sú: prvá=%d, druhá=%d",prva, druha);
    
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 1.5

Napíšte program, ktorý vypočíta BMI (Body Mass Index) z dát zadaných používateľom a vypíše ho.
BMI je vypočítané podľa vzorca:

```text
BMI = Váha (v kg) / Výška^2 (v metroch)
```

### Príklady vstupov / výstupov programu

Ak používateľ zadá výšku 1.82m a váhu 72kg výsledné vypočítané BMI je 21.736506.

```C
#include <stdio.h>

int main()
{
    float vaha;
    float vyska;
    
    printf("Zadajte vašu výšku v metroch: ");
    scanf("%f",&vyska);
    
    printf("Zadajte vašu váhu v kilogramoch: ");
    scanf("%f",&vaha);
    
    float bmi = vaha / (vyska * vyska);
    
    printf("Vaše BMI je %.2f",bmi);
    
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 1.6

Napíšte program, ktorý konvertuje teplotu zadanú v stupňoch Celzia na stupne Fahrenheita a vypíše konvertovanú teplotu.
Vstupná teplota je zadaná používateľom po spustení programu.

Vzorec pre konverziu stupníc teploty vyjadruje vzorec:

```text
fahrenheit = (celsius * 9/5) + 32
```

### Príklady vstupov / výstupov programu

Ak používateľa zadá na vstupe teplotu 20.5 °C výsledná teplota bude vypísaná 68.900002 °F

```C
#include <stdio.h>

int main()
{
    float c,f;
    
    printf("Zadajte teplutu v °C: ");
    scanf("%f",&c);
    
    printf("Teplota vo Fahrenhei stupnici: %.2f°F",(c * 9/5)+32);
    
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 1.7

Cyklista si sleduje prejdenú vzdialenosť v kilometroch a čas (v minútach a sekundách), za ktorý
túto vzdialenosť prešiel. Naprogramujte program, ktorý na základe premenných kilometre, minuty,
sekundy vypočíta cyklistovu priemernú rýchlosť v km/h (kilometre za hodinu) a vypíše ju na
obrazovku. Hodnoty premenných vyžiadajte od používateľa po spustení programu.

### Príklady vstupov / výstupov programu

Napríklad ak kilometre = 8.5, minuty = 25 a sekundy = 30, potom priemerná rýchlosť cyklistu bola
20.0 km/h.

Ak kilometre = 9.7, minuty = 29 a sekundy = 55, potom priemerná rýchlosť cyklistu bola približne
19.454 km/h.

### Riešenie

```C
#include <stdio.h>

int main()
{
    float km;
    int m,s;
    
    printf("Zadajte prejdenú vzdialenosť v km: ");
    scanf("%f",&km);
    
    printf("Zadajte prejdené minuty: ");
    scanf("%d",&m);
    
    printf("Zadajte prejdené sekundy: ");
    scanf("%d",&s);
    
    float celkovy_cas_v_hodinach = (m/60.0)+(s/3600.0);
    
    printf("Vaša priemerná rýchlosť bola %.2f km/h", km/celkovy_cas_v_hodinach);
    
    return 0;
}
```




