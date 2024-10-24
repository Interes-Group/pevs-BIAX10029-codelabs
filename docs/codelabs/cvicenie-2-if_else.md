summary: Cvičenie 2A If-else
id: cvicenie-2a
categories: cvicenie
tags: beginner, with-bonus
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 2A If-Else

<!-- ------------------------ -->
## Úvod

Úlohy v tomto cvičení majú za úlohu precvičiť a ozrejmiť programovanie podmienok a tzv. control flow programu pomocou if-else
výrazov.

### Obsah
- použitie výrazu if pre kontrolu spustenia príkazov programu
- použitie výrazov if-else
- použitie viacero podmienok if-else if-else

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C. Napríklad stránku [OneCompiler for C](https://onecompiler.com/c)

<!-- ------------------------ -->
## Úloha 2.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý nájde maximum z dvoch zadaných čísel.
Čísla môže zadať používateľ štandardným vstupom. Program vypíše svoje zistenie používateľovi. 

### Príklady vstupov / výstupov programu

Ak používateľ zadá ako vstup čísla 5 a 8 tak program vypíše číslo 8 ako maximum.

### Riešenie

```C
#include <stdio.h>

int main() {
    int a, b;

    printf("Zadajte dve čísla oddelené medzerou: ");
    scanf("%d %d", &a, &b);
    if (a < b) {
        printf("%d", b);
    } else {
        printf("%d", a);
    }

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 2.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý rozhodne či zadané číslo je pozitívne, negatívne alebo nula.
Čísla môže zadať používateľ štandardným vstupom. Program po zadaní vstupu vypíše či je číslo pozitívne, negatívne alebo je presne nula.

### Príklady vstupov / výstupov programu

Ak používateľ zadá ako vstup číslo **-5** program vypíše **negatívne**, pre číslo **98** vypíše program **pozitívne** a pre vstup **0** vypíše **nula**.

### Riešenie

```C
#include <stdio.h>

int main() {
    int cislo;

    printf("Zadajte číslo: ");
    scanf("%d", &cislo);

    if (cislo < 0) {
        printf("negatívne", cislo);
    } else if (cislo > 0) {
        printf("pozitívne", cislo);
    } else if (cislo == 0) {
        printf("nula", cislo);
    }
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 2.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý zistí či je zadané číslo párne alebo nepárne.
Čísla môže zadať používateľ štandardným vstupom. Program vypíše zistenie slovom _párne_ alebo _nepárne_ používateľovi.

### Príklady vstupov / výstupov programu

Ak používateľ zadá ako vstup číslo **24**, program vypíše **párne**, ak používateľ zadá číslo **59** program vypíše **nepárne**.

### Riešenie

```C
#include <stdio.h>

int main() {
    int a;

    printf("Zadajte číslo: ");
    scanf("%d", &a);
    if (a % 2 == 0) {
        printf("párne");
    } else {
        printf("nepárne");
    }

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 2.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý zistí či zadaný rok je priestupný.
Rok môže zadať používateľ štandardným vstupom. Program vypíše slovom _priestupný_ alebo _nie je priestupný_ používateľovi.

> aside positive
> Ak by si si nepamätal ako sa zisťuje priestupný rok, môže pomôcť tento odkaz [https://www.calendar-365.com/leap-years.html](https://www.calendar-365.com/leap-years.html).

### Príklady vstupov / výstupov programu

Ak používateľ zadá ako vstup **2016** tak program vypíše **priestupný**, pre zadaný rok **2011** program vypíše **nie je priestupný**.

### Riešenie

```C
#include <stdio.h>

int main() {
    int rok;

    printf("Zadajte rok: ");
    scanf("%d", &rok);

    if(rok % 4 == 0){
        if(rok % 100 == 0) {
            if(rok % 400 == 0) {
                printf("priestupny");
            } else {
                printf("nepriestupny");
            }
        } else {
            printf("priestupny");
        }
    } else {
        printf("nepriestupny");
    }

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 2.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypíše koľko kalendárnych dní má mesiac.
Používateľ cez štandardný vstup zadá číslo mesiaca (1-12) a program používateľovi vypíše koľko kalendárnych dní má zadaný mesiac.
Pre implementáciu programu **požite maximálne 3 podmienky pre výrazy if a else if** a **použite logické operátory**.

### Príklady vstupov / výstupov programu

Ak používateľ zadá ako vstup **5** program vypíše číslo **31**.

### Riešenie

```C
#include <stdio.h>

int main() {
    int mesiac;

    printf("Zadajte mesiac: ");
    scanf("%d", &mesiac);

    if(mesiac == 1 || mesiac == 3 || mesiac == 5 || mesiac == 7 || mesiac == 8 || mesiac == 10 || mesiac == 11){
        printf("31");
    } else if (mesiac == 4 || mesiac == 6 || mesiac == 9 || mesiac == 11) {
        printf("30");
    } else if (mesiac == 2) {
        printf("28 (v priestupný rok 29)");
    } else {
        printf("nezadali ste platný mesiac");
    }

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 2.6

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypočíta účet za elektrinu používateľa 
na základe zadanej spotreby. Spotreba elektriny je zadaná používateľ štandardným vstupom v abstraktných jednotkách.

Účet za elektrinu vypočítajte podľa graduálneho cenníka:

- **Prvých 50 jednotiek** je účtovaných cenou **0.5€/jednotku**.
- **Ďalších 100 jednotiek** je účtovaných cenou **0.75€/jednotku**.
- **Ďalších 100 jednotiek** je účtovaných cenou **1.20€/jednotku**.
- **Nad 250 jednotiek** je účtovaná cena **1.50€/jednotku**.

Pre finálnu sumu **sa vzťahuje daň 20%**, ktorá je pridaná k finálnej sume.

### Príklady vstupov / výstupov programu

Ak používateľ zadá spotrebu elektrickej energie **300 jednotiek** tak finálna cena po zdanení bude **354€**.

### Riešenie

```C
#include <stdio.h>

int main() {
    float units;

    printf("Zadajte vašu spotrebu elektriny: ");
    scanf("%f", &units);

    float price = 0;
    if (units < 50) {
        printf("%.2f€", 0.5 * units * 1.2);
        return 0;
    }
    price += 25; // pretože 50 * 0.25
    units -= 50;

    if (units - 100 <= 0) {
        price += 0.75 * units;
        printf("%.2f€", price * 1.2);
        return 0;
    }
    price += 75; // pretože 100 * 0.75
    units -= 100;

    if (units - 100 <= 0) {
        price += 1.2 * units;
        printf("%.2f€", price * 1.2);
        return 0;
    }
    price += 120; // pretože 100 * 1.2
    units -= 100;

    price += 1.5 * units;
    printf("%.2f€", price * 1.2);

    return 0;
}
```

<!-- ------------------------ -->
## ✨ Bonus Úloha 2.7

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vypíše názov dňa v týždni pre zadané číslo.
Číslo indexu dňa v týždni zadá používateľ štandardným vstupom. Pre implementáciu **môžte použiť iba jeden if výraz**. (Skúste nepoužiť switch výraz).

### Príklady vstupov / výstupov programu

Pre vstup **1** od používateľa program vypíše **Utorok**.

### Riešenie

```C
#include <stdio.h>

char DAY_OF_WEEK[7][10] = {"Pondelok", "Utorok", "Streda", "Štvrtok", "Piatok", "Sobota", "Nedeľa"};

int main() {
    int day;

    printf("Zadajte poradové číslo dňa (začínajúce 0): ");
    scanf("%d", &day);

    if (day >= 0 && day < 7) {
        printf("%s", DAY_OF_WEEK[day]);
    } else {
        printf("Musíte zadať číslo medzi 0 a 6 vrátane");
    }

    return 0;
}
```


