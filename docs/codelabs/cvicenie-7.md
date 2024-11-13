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

Riešenia na jednotlivé úlohy budú uverejnené najskôr.

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

<!-- ------------------------ -->
## Úloha 7.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje pole typu `int[]` o veľkosti _5_.
Prvky poľa definujte pri jeho inicializácii (tzv. statické pole).

Program postupne vypíše všetky prvky pola, kde pre každý prvok vypíše na štandardný výstup reťazec:

`&lt;index prvku>. element of the array &lt;adresa poľa> has address &lt;adresa prvku> with value &lt;hodnota prvku>`

### Príklady vstupov / výstupov programu

Pre pole `[9,8,5,1,3]` program vypíše:

```text
0. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec1 with value 9
1. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec2 with value 8
2. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec3 with value 5
3. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec4 with value 1
4. element of the array 0x7ffda2eeeec1 has address 0x7ffda2eeeec5 with value 3
```

> aside positive
> Všimnite si, že adresy elementov poľa ídu v sekvencií za sebou a adresa 0. elementu je taktiež adresa poľa.

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
