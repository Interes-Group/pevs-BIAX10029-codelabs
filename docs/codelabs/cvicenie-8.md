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

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;

    // Požiadanie používateľa o zadanie čísla
    printf("Enter the number of integers to allocate memory for: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of blocks.\n");
        return 1;
    }

    // Dynamická alokácia pamäte pre n prvkov typu int
    int *array = (int *)malloc(n * sizeof(int));
    if (array == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Inicializácia alokovanej pamäte a výpis hodnôt
    printf("Allocated memory values:\n");
    for (int i = 0; i < n; i++) {
        array[i] = i; // Inicializácia na 0 (voliteľné)
        printf("Value at index %d: %d\n", i, array[i]);
    }

    // Uvoľnenie alokovanej pamäte
    free(array);

    return 0;
}
```

#### Vysvetlenie

1. Vstup od používateľa:
   * Používateľ zadá počet blokov pamäte, ktoré sa majú alokovať (n).

2. Dynamická alokácia pamäte:
   * malloc(n * sizeof(int)) alokuje pamäť pre n prvkov typu int.
   * Funkcia malloc vráti pointer na začiatok alokovanej pamäte, alebo NULL, ak alokácia zlyhá.

3. Kontrola úspešnosti alokácie:
   * Ak malloc vráti NULL, program vypíše chybové hlásenie a ukončí sa.

4. Inicializácia a výpis:
   * Cyklus inicializuje hodnoty na 0 a vypisuje ich (hodnoty sú defaultne nešpecifikované, takže ich inicializácia je voliteľná).

5. Uvoľnenie pamäte:
   * free(array) uvoľní dynamicky alokovanú pamäť, aby sa predišlo úniku pamäte.

#### Príklad výstupu

Vstup: `Enter the number of integers to allocate memory for: 5`

Výstup:
```text
Allocated memory values:
Value at index 0: 0
Value at index 1: 0
Value at index 2: 0
Value at index 3: 0
Value at index 4: 0
```

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

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;

    // Požiadanie používateľa o zadanie počtu prvkov
    printf("Enter the number of integers to allocate memory for: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of blocks.\n");
        return 1;
    }

    // Dynamická alokácia pamäte pre n prvkov typu int
    int *array = (int *)malloc(n * sizeof(int));
    if (array == NULL) {
        printf("Memory allocation failed.\n");
        return 1;
    }

    // Výpis adresy alokovanej pamäte
    printf("Adresa alokovanej pamäte: %p\n", array);

    // Zápis čísel od 1 do n do alokovanej pamäte
    for (int i = 0; i < n; i++) {
        array[i] = i + 1; // Hodnoty od 1 do n
    }

    // Výpis jednotlivých hodnôt a ich adries
    for (int i = 0; i < n; i++) {
        printf("%d. položka: adresa = %p ; hodnota = %d\n", i, &array[i], array[i]);
    }

    // Uvoľnenie alokovanej pamäte
    free(array);

    return 0;
}
```

#### Vysvetlenie

1. Vstup od používateľa:
   * Používateľ zadá počet prvkov, pre ktoré sa má alokovať pamäť (n).

2. Dynamická alokácia pamäte:
   * malloc alokuje pamäť pre n prvkov typu int.
   * Adresa alokovanej pamäte sa vypíše na začiatku.

3. Zápis hodnôt do pamäte:
   * Do každého prvku alokovaného poľa sa zapíše hodnota od 1 po n.

4. Výpis hodnôt a ich adries:
   * Iterácia cez alokovanú pamäť vypíše pre každý prvok:
     * Index.
     * Adresu pamäte, kde sa hodnota nachádza.
     * Hodnotu prvku.

5. Uvoľnenie pamäte:
   * Dynamicky alokovaná pamäť sa uvoľní pomocou free na konci programu.

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

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n;

    // Požiadanie používateľa o počet prvkov
    printf("Zadajte počet prvkov: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Počet prvkov musí byť kladné číslo.\n");
        return 1;
    }

    // Dynamická alokácia pamäte pre n prvkov typu int
    int *array = (int *)malloc(n * sizeof(int));
    if (array == NULL) {
        printf("Nepodarilo sa alokovať pamäť.\n");
        return 1;
    }

    // Zadanie hodnôt od používateľa
    for (int i = 0; i < n; i++) {
        printf("Zadanie %d. prvok: ", i + 1);
        scanf("%d", &array[i]);
    }

    // Výpis adresy alokovanej pamäte
    printf("Adresa alokovanej pamäte: %p\n", array);

    // Výpis hodnôt a ich adries
    for (int i = 0; i < n; i++) {
        printf("%d. položka: adresa = %p ; hodnota = %d\n", i, &array[i], array[i]);
    }

    // Uvoľnenie alokovanej pamäte
    free(array);

    return 0;
}
```

#### Vysvetlenie

1. Vstup od používateľa:
   * Používateľ zadá počet prvkov (n).
   * Kontrola zabezpečí, že zadané číslo je kladné.

2. Dynamická alokácia pamäte:
   * Pomocou malloc sa alokuje pamäť pre n prvkov typu int.

3. Zadanie hodnôt:
   * Cyklus požaduje od používateľa hodnoty pre jednotlivé prvky dynamického poľa.

4. Výpis hodnôt a ich adries:
   * Pre každý prvok sa vypíše jeho index, adresa a hodnota.

5. Uvoľnenie pamäte:
   * Dynamicky alokovaná pamäť sa uvoľní pomocou free na konci programu.


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

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    int n, maxLen;

    // Načítanie počtu slov a maximálnej dĺžky slova od používateľa
    printf("Zadajte počet slov: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Počet slov musí byť kladné číslo.\n");
        return 1;
    }

    printf("Zadajte maximálnu dĺžku slova: ");
    scanf("%d", &maxLen);

    if (maxLen <= 0) {
        printf("Maximálna dĺžka slova musí byť kladné číslo.\n");
        return 1;
    }

    // Alokácia poľa pointerov na reťazce
    char **words = (char **)malloc(n * sizeof(char *));
    if (words == NULL) {
        printf("Nepodarilo sa alokovať pamäť pre pole slov.\n");
        return 1;
    }

    // Načítanie slov od používateľa
    printf("Zadajte slová:\n");
    for (int i = 0; i < n; i++) {
        // Alokácia pamäte pre jednotlivé slovo (s miestom pre '\0')
        words[i] = (char *)malloc((maxLen + 1) * sizeof(char));
        if (words[i] == NULL) {
            printf("Nepodarilo sa alokovať pamäť pre slovo %d.\n", i + 1);
            return 1;
        }

        // Načítanie slova
        printf("Slovo %d: ", i + 1);
        scanf("%s", words[i]);
    }

    // Výpis slov a ich dĺžok
    printf("---\nSlová a ich dĺžky:\n");
    for (int i = 0; i < n; i++) {
        printf("%s (%zu znakov)\n", words[i], strlen(words[i]));
    }

    // Uvoľnenie alokovanej pamäte
    for (int i = 0; i < n; i++) {
        free(words[i]);
    }
    free(words);

    return 0;
}
```

#### Vysvetlenie

1. Vstup od používateľa:
   * Používateľ zadáva počet slov (n) a maximálnu dĺžku slova (maxLen).
   * Oba vstupy sú validované, aby boli kladné.

2. Dynamická alokácia:
   * Pole words je alokované pre n pointerov na reťazce.
   * Pre každý reťazec v poli je alokovaná pamäť veľkosti maxLen + 1 (pre \0).

3. Načítanie slov:
   * Každé slovo je načítané pomocou scanf a uložené v alokovanej pamäti.

4. Výpis slov a ich dĺžok:
   * Funkcia strlen z knižnice <string.h> sa používa na získanie dĺžky reťazca.

5. Uvoľnenie pamäte:
   * Pre každé slovo sa pamäť uvoľní pomocou free, potom sa uvoľní pamäť pre pole pointerov.

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

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

int main() {
    int initial_size = 5; // Počiatočná veľkosť poľa
    int current_size = initial_size; // Aktuálna veľkosť poľa
    int *array = (int *)malloc(current_size * sizeof(int)); // Alokácia pamäte
    if (array == NULL) {
        printf("Nepodarilo sa alokovať pamäť.\n");
        return 1;
    }

    int input, count = 0;

    printf("Zadajte hodnoty (zadaním -1 ukončíte):\n");
    while (1) {
        scanf("%d", &input);
        if (input == -1) {
            break;
        }

        // Ak pole je plné, zväčšiť veľkosť na dvojnásobok
        if (count == current_size) {
            current_size *= 2;
            int *temp = (int *)realloc(array, current_size * sizeof(int));
            if (temp == NULL) {
                printf("Nepodarilo sa zväčšiť pamäť.\n");
                free(array); // Uvoľnenie pôvodnej pamäte
                return 1;
            }
            array = temp;
        }

        // Uloženie hodnoty do poľa
        array[count++] = input;
    }

    // Výpis načítaných hodnôt
    printf("---\nZadané hodnoty: ");
    for (int i = 0; i < count; i++) {
        printf("%d ", array[i]);
    }
    printf("\n");

    // Výpis konečnej veľkosti poľa a adresy
    printf("Konečná veľkosť poľa: %d prvkov\n", current_size);
    printf("Adresa poľa: %p\n", array);

    // Uvoľnenie pamäte
    free(array);

    return 0;
}
```

#### Vysvetlenie

1. Počiatočná veľkosť poľa:
* Pamäť je alokovaná na veľkosť 5 * sizeof(int).

2. Pridávanie hodnôt:
   * Používateľ zadáva čísla, ktoré sa ukladajú do poľa.
   * Ak počet prvkov dosiahne aktuálnu veľkosť poľa, veľkosť sa zdvojnásobí pomocou funkcie realloc.

3. Zväčšenie pamäte:
   * realloc zmení veľkosť alokovanej pamäte na dvojnásobok. 
     realloc je nákladná operácia a tak sa oplatí radšej alokovať dopredu väčšiu časť pamäte ako alokovať po jednom vstupe.
   * Ak alokácia zlyhá, program vypíše chybu a uvoľní existujúcu pamäť.

4. Ukončenie zadávania:
   * Zadanie -1 ukončí zadávanie hodnôt.

5. Výpis výsledkov:
   * Všetky načítané hodnoty sú vypísané spolu s konečnou veľkosťou poľa a adresou.

6. Uvoľnenie pamäte:
   * Alokovaná pamäť je uvoľnená pomocou free.

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

### Riešenie

#### Problémy s funkciou

1. Únik pamäte:
   * Alokovaná pamäť pomocou malloc nie je uvoľnená pred ukončením funkcie. Tým sa stráca možnosť k nej pristúpiť, čo vedie k úniku pamäte.

2. Žiadna kontrola úspešnosti alokácie:
   * Funkcia malloc môže zlyhať a vrátiť NULL. Program toto nezohľadňuje, čo môže spôsobiť segfault alebo nepredvídateľné správanie, ak sa pamäť pokúsi použiť.

#### Opravy

```C
#include <stdio.h>
#include <stdlib.h>

void runMe() {
    // Alokácia pamäte
    int* leakingPtr = (int*) malloc(sizeof(int) * 1024);
    if (leakingPtr == NULL) {
        printf("Nepodarilo sa alokovať pamäť.\n");
        return;
    }

    // Naplnenie pamäte hodnotami
    for (int i = 0; i < 1024; i++) {
        leakingPtr[i] = i + 1000;
    }

    // Použitie alokovaných hodnôt (napr. výpis prvých niekoľkých hodnôt)
    for (int i = 0; i < 5; i++) {
        printf("Value at index %d: %d\n", i, leakingPtr[i]);
    }

    // Uvoľnenie pamäte
    free(leakingPtr);
}

int main() {
    runMe();
    return 0;
}
```

1. Uvoľnenie pamäte:
   * Pridané volanie free(leakingPtr) pred ukončením funkcie runMe zabezpečí, že alokovaná pamäť nebude ponechaná na heap.

2. Kontrola úspešnosti malloc:
   * Pred použitím pointera leakingPtr sa kontroluje, či alokácia bola úspešná (leakingPtr != NULL).

#### Príklad výstupu

```text
Value at index 0: 1000
Value at index 1: 1001
Value at index 2: 1002
Value at index 3: 1003
Value at index 4: 1004
```
