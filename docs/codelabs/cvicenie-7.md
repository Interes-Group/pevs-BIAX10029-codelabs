summary: Cvičenie 7 Pointer
id: cvicenie-7
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 7 - Pointer

<!-- ------------------------ -->
## Úvod

Náplňou tohto cvičenia bude najmä si osvojiť komplexnú problematiku pointerov ich správanie a využitie pri riešení problémov.

Pri týchto cvičenia je dôležité si uvedomiť kedy sa pracuje s hodnotou a kedy s referenciou t.j. s pointerom (adresou) na hodnotu.

### Obsah
- základné práce s pointermi
- práca so statickými poliami
- porovnanie volaní funkcií hodnotou a volaním referenciou

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh odporúčam mať funkčné lokálne vývojové prostredie (VS Code, CLion a pod.) a kompilátor jazyka C.

> aside negative
> Ak v rámci predpísaných výstupov sú uvedené slová medzi znakmi `<` a `>` ide o placeholder pre skutočnú hodnotu, ktorú musí dosadiť program.

Riešenia na jednotlivé úlohy budú uverejnené neskôr.

<!-- ------------------------ -->
## Úloha 7.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje premenné typu _int_ _m_, _n_ a _o_ a pointer _z_, 
ktorý je pointer na premennú _m_. Premennej m priraďte ľubovolnú hodnotu.

Program by mal vypísať na štandardný výstup následné reťazce:

```text
 z stores the address of m  = <aktuálna adresa>                                                                  
                                                                                                              
 *z stores the value of m = <aktuálna hodnota>                                                                                
                                                                                                              
 &m is the address of m = <aktuálna adresa>                                                                      
                                                                                                              
 &n stores the address of n = <aktuálna adresa>                                                                  
                                                                                                              
 &o  stores the address of o = <aktuálna adresa>                                                                 
                                                                                                              
 &z stores the address of z = <aktuálna adresa> 
```

> aside positive
> Všimnite si, že ak program spustíte opakovane adresy premenných sa menia.

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia premenných
    int m, n, o;
    int *z;

    // Priradenie hodnôt
    m = 42; // Ľubovoľná hodnota
    z = &m; // Pointer z ukazuje na premennú m

    // Výpis požadovaných informácií
    printf("z stores the address of m = %p\n", z);
    printf("*z stores the value of m = %d\n", *z);
    printf("&m is the address of m = %p\n", &m);
    printf("&n stores the address of n = %p\n", &n);
    printf("&o stores the address of o = %p\n", &o);
    printf("&z stores the address of z = %p\n", &z);

    return 0;
}
```

#### Vysvetlenie

1. Premenné a pointery:
    * m, n, a o sú premennej typu int. 
    * z je pointer na int, ktorý uchováva adresu premennej m.

2. Priradenie hodnôt:
   * Premennej m priraďujeme hodnotu 42 (môže byť ľubovoľná).
   * Pointer z nastavujeme na adresu premennej m pomocou operátora &.
   
3. Výpis:
   * Adresy a hodnoty sa vypisujú pomocou formátovacieho reťazca %p (pre pointery) a %d (pre hodnotu typu int).

#### Príklady výstupu

Po spustení program môže byť výstup nasledovný (samozrejme adresy líšia medzi spusteniami):

```text
z stores the address of m = 0x7ffcb5e7914c
*z stores the value of m = 42
&m is the address of m = 0x7ffcb5e7914c
&n stores the address of n = 0x7ffcb5e79148
&o stores the address of o = 0x7ffcb5e79144
&z stores the address of z = 0x7ffcb5e79138
```

<!-- ------------------------ -->
## Úloha 7.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje premennú typu _int m_ a _pointer ab_.
Napíšte program tak aby hodnota premennej _m_ menila tak aby vyhovovala nižšie uvedeným výpisom a aby pointer _ab_ ukazoval na hodnotu premennej _m_.

Program by mal vypísať na štandardný výstup nasledovné:

```text
Address of m : <adresa>
Value of m : 29                                                                                              
                                                                                                          
Now ab is assigned with the address of m.                                                                    
Address of pointer ab : <adresa>                                                                       
Content of pointer ab : 29                                                                                   
                                                                                                          
The value of m assigned to 34 now.                                                                           
Address of pointer ab : <adresa>                                                                       
Content of pointer ab : 34                                                                                   
                                                                                                          
The pointer variable ab is assigned with the value 7 now.                                                    
Address of m : <adresa>                                                                                
Value of m : 7 
```

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia premennej a pointeru
    int m;
    int *ab;

    // Nastavenie počiatočnej hodnoty premennej m
    m = 29;
    printf("Address of m : %p\n", &m);
    printf("Value of m : %d\n", m);

    // Nastavenie pointeru ab na adresu premennej m
    ab = &m;
    printf("\nNow ab is assigned with the address of m.\n");
    printf("Address of pointer ab : %p\n", ab);
    printf("Content of pointer ab : %d\n", *ab);

    // Zmena hodnoty m cez pointer
    m = 34;
    printf("\nThe value of m assigned to 34 now.\n");
    printf("Address of pointer ab : %p\n", ab);
    printf("Content of pointer ab : %d\n", *ab);

    // Zmena hodnoty premennej m priamo cez pointer ab
    *ab = 7;
    printf("\nThe pointer variable ab is assigned with the value 7 now.\n");
    printf("Address of m : %p\n", &m);
    printf("Value of m : %d\n", m);

    return 0;
}
```

##### Vysvetlenie

1. Premenné a pointery:
   * m je premenná typu int.
   * ab je pointer na int, ktorý ukazuje na adresu premennej m.

3. Počiatočné hodnoty:
    * Premenná m je inicializovaná hodnotou 29.

3. Pointer priraďuje adresu:
    * Pointer ab je nastavený na adresu premennej m pomocou operátora &.

4. Zmena hodnoty m:
    * Hodnota m je priamo zmenená a výpis potvrdzuje adresu a obsah cez pointer.

5. Zmena cez pointer:
    * Hodnota premennej m je zmenená priamo pomocou pointera ab s použitím operátora dereferencie *.

#### Príklad výstupu

Pri spustení programu môže byť výstup nasledovný (adresy sa môžu líšiť podľa systému):

```text
Address of m : 0x7ffc7d9d314c
Value of m : 29

Now ab is assigned with the address of m.
Address of pointer ab : 0x7ffc7d9d314c
Content of pointer ab : 29

The value of m assigned to 34 now.
Address of pointer ab : 0x7ffc7d9d314c
Content of pointer ab : 34

The pointer variable ab is assigned with the value 7 now.
Address of m : 0x7ffc7d9d314c
Value of m : 7
```

<!-- ------------------------ -->
## Úloha 7.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý pomocou operátorov `&` a `*` vypíše nižšie uvedené reťazce.
Program definuje premennú _int m_, _float f_ a _char c_ inicializované na nasledovné hodnoty:

- m = 300
- f = 256.450001
- c = "z"

> aside positive
> Pamätajte, že operátor & je na získanie adresy premennej a operátor * na získanie hodnoty uloženej na adrese.

Program by mal vypísať na štandardný výstup nasledovné:

```text
m = <hodnota>                                                                                                      
fx = <hodnota>                                                                                           
cht = <hodnota>                                                                                                      
                                                                                                          
Using & operator :                                                                                           
-----------------------                                                                                       
address of m = <adresa>                                                                                
address of fx = <adresa>                                                                               
address of cht = <adresa>                                                                              
                                                                                                          
Using & and * operator :                                                                                     
-----------------------------                                                                                 
value at address of m = <hodnota>                                                                                  
value at address of fx = <hodnota>                                                                          
value at address of cht = <hodnota>                      

Using only pointer variable :                                                                                
----------------------------------                                                                            
address of m = <adresa>                                                                                
address of fx = <adresa>                                                                               
address of cht = <adresa>                                                                              
                                                                                                          
Using only pointer operator :                                                                                
----------------------------------                                                                            
value at address of m = <hodnota>                                                                                  
value at address of fx= <hodnota>                                                                           
value at address of cht= <hodnota> 
```

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia a inicializácia premenných
    int m = 300;
    float f = 256.450001;
    char c = 'z';

    // Pointery na jednotlivé premenné
    int *p_m = &m;
    float *p_f = &f;
    char *p_c = &c;

    // Výpis hodnôt premenných
    printf("m = %d\n", m);
    printf("fx = %.6f\n", f);
    printf("cht = %c\n\n", c);

    // Použitie operátora &
    printf("Using & operator :\n");
    printf("-----------------------\n");
    printf("address of m = %p\n", &m);
    printf("address of fx = %p\n", &f);
    printf("address of cht = %p\n\n", &c);

    // Použitie operátorov & a *
    printf("Using & and * operator :\n");
    printf("-----------------------------\n");
    printf("value at address of m = %d\n", *(&m));
    printf("value at address of fx = %.6f\n", *(&f));
    printf("value at address of cht = %c\n\n", *(&c));

    // Použitie iba pointerových premenných
    printf("Using only pointer variable :\n");
    printf("----------------------------------\n");
    printf("address of m = %p\n", p_m);
    printf("address of fx = %p\n", p_f);
    printf("address of cht = %p\n\n", p_c);

    // Použitie iba pointerových operátorov
    printf("Using only pointer operator :\n");
    printf("----------------------------------\n");
    printf("value at address of m = %d\n", *p_m);
    printf("value at address of fx = %.6f\n", *p_f);
    printf("value at address of cht = %c\n", *p_c);

    return 0;
}
```

#### Vysvetlenie

1. Premenné a pointery:
   * m, f, a c sú premenné typu int, float, a char inicializované na zadané hodnoty.
   * Pointery p_m, p_f, a p_c uchovávajú adresy týchto premenných.

2. Použitie operátora &:
    * Operátor & sa používa na získanie adresy premenných.

3. Použitie operátorov & a *:
    * Kombinácia & a * umožňuje získať hodnotu na adrese priamo cez ukazovateľ.

4. Použitie pointerových premenných:
    * Použitím samotných pointerov vypisujeme adresy premenných.

5. Použitie pointerových operátorov:
    * Operátor * (dereferencovanie) umožňuje prístup k hodnote na adrese, na ktorú ukazuje pointer.

#### Príklad výstupu

Pri spustení programu môže byť výstup nasledovný (adresy sa môžu líšiť v závislosti od systému):

```text
m = 300
fx = 256.450001
cht = z

Using & operator :
-----------------------
address of m = 0x7ffc7d9d314c
address of fx = 0x7ffc7d9d3150
address of cht = 0x7ffc7d9d3154

Using & and * operator :
-----------------------------
value at address of m = 300
value at address of fx = 256.450001
value at address of cht = z

Using only pointer variable :
----------------------------------
address of m = 0x7ffc7d9d314c
address of fx = 0x7ffc7d9d3150
address of cht = 0x7ffc7d9d3154

Using only pointer operator :
----------------------------------
value at address of m = 300
value at address of fx = 256.450001
value at address of cht = z
```

<!-- ------------------------ -->
## Úloha 7.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý obsahuje funkciu ,ktorá spočíta dve čísla.
Funkciu implementujte tak aby prijímala ako argumenty dva pointre typu `int*` (t.j. volanie referenciou - call by reference)
a vrátila číslo typu _int_ (pozor nie pointer!).

Funkciu následne zavolajte s rôznymi vstupmi.

### Príklady vstupov / výstupov programu

- pre čísla 5 a 6 program vypíše:
```text
Function called with pointer <adresa> with value 5 and pointer <adresa> with value 6.
The sum of the numbers is 11.
```

- pre čísla 74 a -23 program vypíše:
```text
Function called with pointer <adresa> with value 74 and pointer <adresa> with value -23.
The sum of the numbers is 51.
```

### Riešenie

```C
#include <stdio.h>

// Funkcia na spočítanie dvoch čísel pomocou pointerov
int addNumbers(int *a, int *b) {
    // Výpis adries a hodnôt argumentov
    printf("Function called with pointer %p with value %d and pointer %p with value %d.\n", a, *a, b, *b);

    // Návrat súčtu hodnôt, na ktoré ukazujú pointery
    return *a + *b;
}

int main() {
    // Premenné na testovanie
    int num1 = 5, num2 = 6;
    int num3 = 74, num4 = -23;

    // Prvé volanie funkcie
    int sum1 = addNumbers(&num1, &num2);
    printf("The sum of the numbers is %d.\n\n", sum1);

    // Druhé volanie funkcie
    int sum2 = addNumbers(&num3, &num4);
    printf("The sum of the numbers is %d.\n", sum2);

    return 0;
}
```

#### Vysvetlenie

1. Funkcia addNumbers:
   * Funkcia prijíma dva pointery typu int*.
   * Vypisuje adresy a hodnoty, na ktoré ukazujú pointery.
   * Vracia súčet hodnôt, na ktoré ukazujú pointery.

2. Hlavný program:
    * Definované sú premenné num1, num2, num3, a num4.
   * Volanie funkcie addNumbers s adresami premenných pomocou operátora &.
   * Výstup obsahuje informácie o pointeroch, hodnotách a výslednom súčte.

3. Dôležité:
    * Operátor & sa používa na získanie adresy premenných.
   * Dereferencovanie * vráti hodnotu na adrese, na ktorú ukazuje pointer.

#### Príklad výstupu

Pri spustení programu bude výstup nasledovný:

```text
Function called with pointer 0x7ffcd3b9b41c with value 5 and pointer 0x7ffcd3b9b418 with value 6.
The sum of the numbers is 11.

Function called with pointer 0x7ffcd3b9b414 with value 74 and pointer 0x7ffcd3b9b410 with value -23.
The sum of the numbers is 51.
```

<!-- ------------------------ -->
## Úloha 7.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje pole typu `int[]` o veľkosti _5_.
Prvky poľa definujte pri jeho inicializácii (tzv. statické pole).

Program postupne vypíše všetky prvky pola, kde pre každý prvok vypíše na štandardný výstup reťazec:

`&lt;index prvku>. element of the array &lt;adresa poľa> has address &lt;adresa prvku> with value &lt;hodnota prvku>`

### Príklady vstupov / výstupov programu

Pre pole `[9,8,5,1,3]` program vypíše:

```text
0. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec0 with value 9
1. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec4 with value 8
2. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec8 with value 5
3. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeecc with value 1
4. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeed0 with value 3
```

> aside positive
> Všimnite si, že adresy elementov poľa ídu v sekvencií za sebou a adresa 0. elementu je taktiež adresa poľa.

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia a inicializácia poľa
    int array[5] = {10, 20, 30, 40, 50};

    // Prechádzanie poľa a výpis požadovaných informácií
    for (int i = 0; i < 5; i++) {
        printf("%d. element of the array %p has address %p with value %d\n", i, array, &array[i], array[i]);
    }

    return 0;
}
```

#### Vysvetlenie

1. Definícia a inicializácia poľa:
    * Pole array je staticky definované s veľkosťou 5 a inicializované hodnotami {10, 20, 30, 40, 50}.

2. Iterácia cez pole:
    * for cyklus prechádza všetky indexy poľa od 0 po 4.

3. Výpis informácií:
    * Pre každý prvok poľa sa vypíše:
      * Index prvku (i).
      * Adresa samotného poľa (array).
      * Adresa konkrétneho prvku (&array[i]).
      * Hodnota prvku (array[i]).

4. Formátovanie:
    * %d sa používa na hodnoty typu int.
    * %p na výpis adries. Adresy sa pretypujú na (void *) pre kompatibilitu so štandardom %p.

<!-- ------------------------ -->
## Úloha 7.6

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje funkciu pre výpočet dĺžky reťazca.
Funkcia má jeden argument typu `char*` , ktorý vyjadruje reťacez znakov. Funkcia vracia hodnotu typu `int`, ktorá sa rovná počtu znakov vo vstupnom reťazci.
Pre implementáciu **nepoužite** knižnicu _<string.h>_ ani žiadnu inú okrem _<stdio.h>_.

Pri implementácií použitie inkrementáciu pointrov, resp. pričítanie čísla (_int_) k pointru.

> aside positive
> Pamätajte, že každý reťazec je ukončený znakom _\0_.

### Príklady vstupov / výstupov programu

- pre vstupný reťacez "Milan" funkcia vráti 5
- pre vstupný reťacez "Cvicenie7" funkcia vráti 9
- pre vstupný reťacez "" funkcia vráti 0

### Riešenie

```C
#include <stdio.h>

// Funkcia na výpočet dĺžky reťazca
int stringLength(char *str) {
    int length = 0;

    // Inkrementácia pointeru, kým nedosiahne nulový znak '\0'
    while (*str != '\0') {
        length++;
        str++; // Posun pointera na ďalší znak
    }

    return length;
}

int main() {
    // Testovacie reťazce
    char str1[] = "Milan";
    char str2[] = "Cvicenie7";
    char str3[] = "";

    // Výstupy funkcie pre rôzne vstupy
    printf("The length of the string \"%s\" is %d\n", str1, stringLength(str1));
    printf("The length of the string \"%s\" is %d\n", str2, stringLength(str2));
    printf("The length of the string \"%s\" is %d\n", str3, stringLength(str3));

    return 0;
}
```

#### Vysvetlenie

1. Funkcia stringLength:
   * Prijíma jeden argument typu char*, ktorý ukazuje na reťazec znakov.
   * Používa while cyklus na iteráciu cez znaky reťazca.
   * Pointer str sa posúva na ďalšiu pozíciu pomocou str++, kým nedosiahne koncový nulový znak '\0'.
   * Premenná length sa inkrementuje pri každom kroku, čím uchováva počet znakov v reťazci.

2. Hlavný program:
   * Testuje funkciu s rôznymi vstupnými reťazcami vrátane prázdneho reťazca.
   * Výsledky funkcie sa vypisujú na štandardný výstup.

3. Obmedzenia:
   * Funkcia nevyžaduje žiadne externé knižnice okrem <stdio.h>.
   * Reťazec musí byť ukončený nulovým znakom '\0' (čo je štandard pre reťazce v C).

<!-- ------------------------ -->
## Úloha 7.7

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje statické pole ľubovolnej veľkosti typu `int[]`
a následne vypíše všetky jeho elementy odzadu, t.j. od posledného k prvému, t.j. od _indexu <dĺžka poľa> - 1_ po _index 0_.
Každý element poľa je vypísaný do nového riadku.

### Príklady vstupov / výstupov programu

Pre pole `[9,8,5,1,3]` program vypíše:

```text
3
1
5
8
9
```

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia statického poľa
    int array[] = {10, 20, 30, 40, 50}; // Ľubovoľné hodnoty
    int size = sizeof(array) / sizeof(array[0]); // Počet prvkov v poli

    // Výpis prvkov poľa odzadu
    printf("Array elements in reverse order:\n");
    for (int i = size - 1; i >= 0; i--) {
        printf("%d\n", array[i]);
    }

    return 0;
}
```

#### Vysvetlenie

1. Definícia poľa:
   * Pole array[] je inicializované s ľubovoľnými hodnotami, napr. {10, 20, 30, 40, 50}.

2. Výpočet veľkosti poľa:
   * sizeof(array) vráti celkovú veľkosť poľa v bajtoch.
   * sizeof(array[0]) vráti veľkosť jedného prvku poľa.
   * size sa vypočíta ako počet prvkov v poli: sizeof(array) / sizeof(array[0]).

3. Iterácia cez pole odzadu:
   * Cyklus for iteruje od posledného indexu (size - 1) po prvý index (0).
   * Prvky sa vypisujú pomocou printf na samostatné riadky.

#### Príklad výstupu

Pri inicializácii poľa int array[] = {10, 20, 30, 40, 50}; bude výstup nasledovný:

```text
Array elements in reverse order:
50
40
30
20
10
```

<!-- ------------------------ -->
## Úloha 7.8

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý zoradí hodnoty staticky definovaného pola typu `int[]`
od najmenšej hodnoty po najväčšiu. Elementy poľa sú zoraďované v definovanom poli, **nevytvárajte** nové pole.
Po zoradení program vypíše postupne všetky elementy poľa za sebou v jednom riadku.

> aside positive
> Pre prehodenie dvoch čísel je potrebná tretia pomocná premenná.

### Príklady vstupov / výstupov programu

Pre pole `[9,8,5,1,3]` program vypíše:

```text
1, 3, 5, 8, 9
```

### Pomôcka

Skúste najprv prísť na implementáciu bez tejto pomoci. Ak by ste sa však nevedeli pohnúť [obrázok na tomto odkaze opisuje algoritmus zoradenia](https://www.w3resource.com/w3r_images/c-pointer-exercise-14-image.png).

### Riešenie

```C
#include <stdio.h>

int main() {
    // Definícia a inicializácia statického poľa
    int array[] = {34, 7, 23, 32, 5, 62};
    int size = sizeof(array) / sizeof(array[0]); // Veľkosť poľa

    // Bubble sort na zoradenie poľa
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {
            if (array[j] > array[j + 1]) {
                // Výmenná operácia
                int temp = array[j];
                array[j] = array[j + 1];
                array[j + 1] = temp;
            }
        }
    }

    // Výpis zoradeného poľa
    printf("Sorted array: ");
    for (int i = 0; i < size; i++) {
        printf("%d ", array[i]);
    }
    printf("\n");

    return 0;
}
```

#### Vysvetlenie

1. Definícia poľa:
   * Pole array[] je inicializované s ľubovoľnými hodnotami, napr. {34, 7, 23, 32, 5, 62}.

2. Výpočet veľkosti poľa:
   * sizeof(array) určuje veľkosť poľa v bajtoch.
   * sizeof(array[0]) určuje veľkosť jedného prvku poľa.
   * Veľkosť poľa je teda size = sizeof(array) / sizeof(array[0]).

3. Bubble sort algoritmus:
   * Dvojitý cyklus iteruje cez pole.
   * Ak je aktuálny prvok väčší ako nasledujúci, hodnoty sa vymenia.
   * Tento proces sa opakuje, až kým pole nie je zoradené.

4. Výpis poľa:
   * Po zoradení sa prvky poľa vypisujú v jednom riadku oddelené medzerami.

#### Príklad výstupu

Pri inicializácii poľa int array[] = {34, 7, 23, 32, 5, 62}; bude výstup:

```text
Sorted array: 5 7 23 32 34 62
```
