summary: Cvičenie 4 Zapúzdrenie a Zovšeobecnenie
id: cvicenie-4
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 4 - Zapúzdrenie a zovšeobecnenie

<!-- ------------------------ -->
## Úvod

Na tomto cvičení si prejdeme pár príkladov pre využitie funkcií, ktoré boli predstavené v cvičení 3. 
Ide o využitie funkcií pre programovacie techniky zapúzdrenia a zovšeobecnenia.

### Obsah
- úloha na zapúzdrenie
- úloha na zovšeobecnenie známej funkcie

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

Pre vypracovanie týchto úloh úplne postačuje použitie online kompilátora jazyku C. Napríklad stránku [OneCompiler for C](https://onecompiler.com/c)

<!-- ------------------------ -->
## Úloha 4.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý sčíta čísla od 1 do 10 a súčet vypíše na obrazovku.
Celý program napíšte v hlavnej funkcií _main_. Výsledok súčtu vypíšte na obrazovku používateľovi.

Očakávaný výsledok je číslo 55.

### Riešenie

```C
#include <stdio.h>

int main() {
    int sum = 0;
    for (int i = 1; i <= 10; ++i) {
        sum += i;
    }
    printf("sum 1-10 = %d", sum);

    return 0;
}
```

<!-- ------------------------ -->
## Úloha 4.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, v ktorom zapúzdrite funkciu súčtu z úlohy 4.1 do funkcie
_int suma()_ . Funkciu zavolajte z hlavnej funkcie _main_, aby sa spustila. Výsledok, ktorý vráti funkcia vypíšte na obrazovku používateľovi.

### Riešenie

```C
#include <stdio.h>

int sum(){
    int sum = 0;
    for (int i = 1; i <= 10; ++i) {
        sum += i;
    }
    printf("sum 1-10 = %d", sum);
}

int main() {
    sum();
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 4.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, v ktorom zovšeobecnite funkciu z úlohy 4.2, 
tak aby vrátila súčet čísel od 1 po N. Funkciu zavolajte z hlavnej funkcie _main_ s rôznymi hodnotami pre vstupný parameter.
Výsledky, ktoré vráti funkcia vypíšte na obrazovku používateľovi.

Všimnite si, že pre parameter s hodnotou **10** sa program správa rovnako ako verzia v úlohe 4.2.

### Príklady vstupov / výstupov programu

- pre **vstup 5** funkcia vráti číslo **15**
- pre **vstup 13** funkcia vráti číslo **91**
- pre **vstup 7** funkcia vráti číslo **28**

### Riešenie

```C
#include <stdio.h>

int sum(int limit){
    int sum = 0;
    for (int i = 1; i <= limit; ++i) {
        sum += i;
    }
    printf("sum 1-%d = %d\n", limit, sum);
}

int main() {
    sum(5);
    sum(13);
    sum(7);
    return 0;
}
```

<!-- ------------------------ -->
## Úloha 4.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, v ktorom zovšeobecnite funkciu suma z úlohy 4.3,
tak aby vrátila súčet K-tych mocnín čísel od 1 po N. Funkciu zavolajte z hlavnej funkcie _main_ s rôznymi hodnotami pre vstupný parameter.
Výsledky, ktoré vráti funkcia vypíšte na obrazovku používateľovi.

Pre voľbu parametra **k = 1** sa program správa rovnako ako predošlá verzia z úlohy 4.3.

### Príklady vstupov / výstupov programu

- pre **vstupy K = 1, N = 7** funkcia vráti číslo **28**
- pre **vstupy K = 3, N = 5** funkcia vráti číslo **225**

### Riešenie

```C
#include <stdio.h>

int sum(int k, int n) {
    int suma = 0;
    for (int i = 1; i <= n; ++i) {
        int mocnina = 1;
        for (int j = 0; j < k; j++) {
            mocnina *= i;
        }
        suma += mocnina;
    }
    printf("súčet %d-tych mocnín čísel 1-%d = %d\n", k, n, suma);
}

int main() {
    sum(1,7);
    sum(3,5);
    return 0;
}
```

### Riešenie 2

```C
#include <stdio.h>
#include <math.h>

int sum(int k, int n) {
    int suma = 0;
    for (int i = 1; i <= n; ++i) {
        suma += pow(i,k);
    }
    printf("súčet %d-tych mocnín čísel 1-%d = %d\n", k, n, suma);
}

int main() {
    sum(1,7);
    sum(3,5);
    return 0;
}
```
