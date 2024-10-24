summary: Cvičenie 3 Funkcie
id: cvicenie-3
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 3 Funkcie

<!-- ------------------------ -->
## Úvod

Na tomto cvičení si prejdeme vytváranie a používanie funkcií.

### Obsah
- definovanie rôznych funkcií 
- volania vlastných funkcií

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C. Napríklad stránku [OneCompiler for C](https://onecompiler.com/c)

<!-- ------------------------ -->
## Úloha 3.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int tretia_mocnina(int a)_**, ktorá má 1 vstupný parameter, číslo _a_. Funkcia pre vstupný
parameter a vráti hodnotu tretiu mocninu parametra _a_.

### Príklady vstupov / výstupov programu

- Volanie funkcie so vstupným argumentom hodnoty 1, t.j. volanie tretia_mocnina(1), vráti hodnotu
  1, pretože 1\*1\*1 = 1.
- Volanie funkcie so vstupným argumentom hodnoty 2, t.j. volanie tretia_mocnina(2), vráti hodnotu
  8, pretože 2\*2\*2 = 8.
- Volanie funkcie so vstupným argumentom hodnoty 3, t.j. volanie tretia_mocnina(3), vráti hodnotu
  27, pretože 3\*3\*3 = 27.

### Riešenie

```C
#include <stdio.h>

int tretia_mocnina(int a) {
    return a * a * a;
}

int main() {

    printf("%d\n", tretia_mocnina(1));
    printf("%d\n", tretia_mocnina(2));
    printf("%d\n", tretia_mocnina(3));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Upravte funkciu **_double priemer_troch(int a, int b, int c)_** z predošlej úlohy tak, aby vrátila aritmetický priemer týchto
3 parametrov, teda hodnotu _(a+b+c)/3_.

### Príklady vstupov / výstupov programu

- Volanie funkcie priemer_troch(1,2,3) vráti hodnotu 2.0, pretože (1+2+3)/3 = 2.0.
- Volanie funkcie priemer_troch(1,2,4.5) vráti hodnotu 2.5, pretože (1+2+4.5)/3 = 2.5.

### Riešenie

```C
#include <stdio.h>

float priemer_troch(float a, float b, float c) {
    return (a + b + c) / 3.0;
}

int main() {

    printf("%.2f\n", priemer_troch(1, 2, 3));
    printf("%.2f\n", priemer_troch(1, 2, 4.5));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int minimum_dvoch(int a, int b)_** s 2 parametrami, číslami _a_ a _b_. Funkcia vráti minimum z
týchto 2 čísiel.

### Príklady vstupov / výstupov programu

- Volanie minimum_dvoch(2,5) vráti hodnotu 2
- Volanie minimum_dvoch(5,5) vráti hodnotu 5
- Volanie minimum_dvoch(-2,-105) vráti hodnotu -105

### Riešenie

```C
#include <stdio.h>

int minimum_dvoch(int a, int b) {
    if (a < b) return a;
    return b;
}

int main() {

    printf("%d\n", minimum_dvoch(2,5));
    printf("%d\n", minimum_dvoch(5,5));
    printf("%d\n", minimum_dvoch(-2,-105));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int pocet_rovnakych(int a, int b, int c)_** s 3 parametrami, číslami _a,b,c_. 

- Funkcia vráti číslo 3, ak sú všetky tri čísla _a,b,c_ rovnaké.
- Vráti číslo 2 ak sú dve z čísel a,b,c rovnaké a tretie číslo je iné.
- Vráti číslo 0, ak sú všetky tri čísla rôzne.

### Príklady vstupov / výstupov programu

- Volanie pocet_rovnakych(2,5,8) vráti hodnotu 0.
- Volanie pocet_rovnakych(1,2,1) vráti 2
- Volanie pocet_rovnakych(10,10,10) vráti 3.

### Riešenie

```C
#include <stdio.h>

int pocet_rovnakych(int a, int b, int c){
    if(a != b && a != c && b != c) return 0;
    if(a == b && b == c) return 3;
    if(a == b || a == c || b == c) return 2;
}

int main() {

    printf("%d\n", pocet_rovnakych(2,5,8));
    printf("%d\n", pocet_rovnakych(1,2,1));
    printf("%d\n", pocet_rovnakych(10,10,10));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int pocet_delitelnych_5(int n)_**, ktorá má vstupný parameter celé nezáporné číslo _n_.
Funkcia načíta n čísiel z klávesnice a vráti počet načítaných čísiel, ktoré boli deliteľné číslom 5.
Ošetrite situáciu, ak by bola funkcia volaná so záporným vstupom! V takom prípade nech funkcia
vypíše, že vstupný argument musí byť nezáporné číslo a vráti hodnotu -1.

### Príklady vstupov / výstupov programu

- Volanie pocet_delitelnych_5(5) načíta 5 čísiel z klávesnice. Ak čísla sú napríklad 5,10,3,4,0 funkcia
  vráti číslo 3 (pretože 5, 10 a 0 sú deliteľné 5).
- Volanie pocet_delitelnych_5(4) načíta 4 čísla z klávesnice. Ak čísla sú napríklad 1,2,3,4 funkcia
  vráti číslo 0 (pretože ani jedno z čísiel nie je deliteľné 5).
- Volanie pocet_delitelnych_5(-3) vypíše, že vstupný argument musí byť nezáporné číslo a vráti číslo
  -1.

### Riešenie

```C
#include <stdio.h>

int pocet_delitelnych_5(int n) {
    if (n < 0) {
        printf("Vstupný argument n musí byť nezáporné číslo\n");
        return -1;
    }
    int count = 0;
    for (int i = 0; i < n; i++) {
        printf("Zadajte ľubovolné číslo: ");
        int input;
        scanf("%d", &input);
        if (input % 5 == 0) count++;
    }
    return count;
}

int main() {

    printf("%d\n", pocet_delitelnych_5(5));
    printf("%d\n", pocet_delitelnych_5(4));
    printf("%d\n", pocet_delitelnych_5(-3));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.6

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int sucet_nacitanych(int n)_**, ktorá má vstupný parameter nezáporné číslo _n_. Funkcia
načíta n čísiel z klávesnice a vráti súčet načítaných čísiel. V prípade, že _n_ je záporné číslo funkcia
vypíše príslušnú chybovú správu a vráti hodnotu -1. V prípade, že _n_ je nula, funkcia vráti hodnotu 0.

### Príklady vstupov / výstupov programu

- Volanie sucet_nacitanych(-1) vypíše chybovú správu, že hodnota n je záporná a vráti -1.
- Volanie sucet_nacitanych(4) načíta 4 čísla z klávesnice. Ak by čísla boli napríklad 5, -2, 10, -7,
  funkcia vráti 6, pretože 5 + (-2) + 10 + (-7) = 6.

### Riešenie

```C
#include <stdio.h>

int sucet_nacitanych(int n) {
    if (n < 0) {
        printf("paramter n nemôže byť záporné číslo\n");
        return -1;
    }
    if (n == 0) return 0;
    int sum = 0;
    for (int i = 0; i < n; ++i) {
        int input;
        printf("Zadaj %d. cislo: ", i + 1);
        scanf("%d", &input);
        sum += input;
    }
    return sum;
}

int main() {

    printf("%d\n", sucet_nacitanych(-1));
    printf("%d\n", sucet_nacitanych(4));

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 3.7

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int druhe_najvacsie(int n)_** s parametrom celé číslo _n_. Funkcia načíta n čísiel z
klávesnice a vráti druhé najväčšie načítané číslo (druhé maximum). V prípade, že má parameter _n_
hodnotu menšiu ako 2, funkcia vypíše chybovú hlášku, že hodnota vstupného argumentu funkcie
musí byť aspoň 2 a ukončí program.

### Príklady vstupov / výstupov programu

- Volanie druhe_najvacsie(1) vypíše chybu a skončí.
- Volanie druhe_najvacsie(5) načíta 5 čísiel z klávesnice. Ak sú tieto čísla napríklad 5,-2,1,2,3
  funkcia vráti číslo 3, pretože -2 ≤ 1 ≤ 2 ≤ 3 ≤ 5
- Volanie druhe_najvacsie(3) načíta 3 čísla z klávesnice. Ak sú tieto čísla napríklad -10, -5, 0 funkcia
  vráti číslo -5, pretože -10 ≤ -5 ≤ 0

### Riešenie

```C
#include <stdio.h>
#include <limits.h>

int druhe_najvacsie(int n) {
    if (n < 2) {
        printf("Chyba: hodnota vstupného argumentu musí byť aspoň 2.\n");
        return -1;
    }

    int max1 = INT_MIN;  // Najväčšie číslo
    int max2 = INT_MIN;  // Druhé najväčšie číslo
    int num;

    for (int i = 0; i < n; i++) {
        printf("Číslo %d: ", i + 1);
        scanf("%d", &num);

        // Ak je nové číslo väčšie ako max1, posunieme max1 do max2
        if (num > max1) {
            max2 = max1;
            max1 = num;
        }
            // Ak je nové číslo menšie ako max1, ale väčšie ako max2
        else if (num > max2 && num != max1) {
            max2 = num;
        }
    }

    if (max2 == INT_MIN) {
        printf("Nie je možné určiť druhé najväčšie číslo.\n");
        return -1;
    }

    return max2;
}

int main() {

    int output = druhe_najvacsie(5);
    if (output == -1) return 1;
    else printf("%d\n", output);

    output = druhe_najvacsie(3);
    if (output == -1) return 1;
    else printf("%d\n", output);

    output = druhe_najvacsie(1);
    if (output == -1) return 1;
    else printf("%d\n", output);

    return 0;
}
```

<!-- ------------------------ -->
## ✨ Bonus Úloha 3.8

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte všeobecnejšiu verziu funkciu z úlohy 3.5, **_int pocet_delitelnych(int n, int k)_**. Funkcia má 2
vstupné parametre, nezáporné celé číslo _n_ a kladné číslo _k_. Ošetrite situáciu, že by vstupný
argument pre parameter _n_ bolo záporné číslo alebo že by vstupný argument pre parameter _k_ bolo
záporné číslo alebo nula – vždy vypíšte príslušnú chybovú hlášku a funkcia vráti hodnotu -1. V
prípade, že sú vstupné argumenty v poriadku, funkcia načíta n čísiel a vráti počet načítaných čísiel,
ktoré boli deliteľné číslom k.

### Príklady vstupov / výstupov programu

- Volanie pocet_delitelnych(5,2) načíta 5 čísiel z klávesnice a vráti koľko z nich je deliteľných 2. Ak
čísla sú napríklad 5,10,3,4,0 funkcia vráti číslo 3 (pretože 10, 4 a 0 sú deliteľné 2).
- Volanie pocet_delitelnych(4,0) vypíše chybovú správu, že hodnota k nie je kladná a vráti -1.
- Volanie pocet_delitelnych(-1,2) vypíše chybovú správu, že hodnota n je záporná a vráti -1.
- Volanie pocet_delitelnych(-1,-2) vypíše chybovú správu, že hodnota n je záporná a že hodnota k nie
je kladná a vráti -1.

<!-- ------------------------ -->
## ✨ Bonus Úloha 3.9

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int delitelnost(int a, int d)_** so vstupnými parametrami kladnými celými číslami _a_ a _d_.
Funkcia vráti hodnotu **1** ak _d_ delí _a_, inak vráti hodnotu **0**. V tejto úlohe nemusíte ošetrovať
korektnosť parametrov _a_ a _d_.

> aside positive
> Pomôcka: Číslo d delí číslo a vtedy, ak zvyšok a po delení d je rovný nule.

### Príklady vstupov / výstupov programu

- Volanie delitelnost(6,3) vráti hodnotu 1, pretože 3 delí 6.
- Volanie delitelnost(7,3) vráti hodnotu 0, pretože 3 nedelí 7.

## ✨ Bonus Úloha 3.10

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý realizuje nasledovnú činnosť.
Definujte funkciu **_int je_prvocislo(int a)_** so vstupným parametrom kladným číslom _a_, ktorá vráti hodnotu
1, ak je parameter _a_ prvočíslo. Ak je a zložené číslo, funkcia vráti hodnotu 0. Môžete
predpokladať, že _a_ bude mať vždy hodnotu aspoň 2. V implementácii funkcie je_prvocislo(a)
využite funkciu delitelnost() z predošlej úlohy!

> aside positive
> Celé číslo a > 2 je prvočíslo, ak pre všetky čísla od 2 po a-1 platí, že nedelia číslo a. Číslo 2 je prvočíslo automaticky.

### Príklady vstupov / výstupov programu

- Volanie je_prvocislo(7) vráti hodnotu True, pretože 7 je prvočíslo, pretože ho nedelí žiadne z čísiel
  2,3,4,5,6.
- Volanie je_prvocislo(8) vráti hodnotu False, pretože 8 nie je prvočíslo. Z čísiel 2,3,4,5,6,7 ho delia
  čísla 2 a 4.
- Volanie je_prvocislo(2) vráti hodnotu True, pretože 2 je prvočíslo. 
