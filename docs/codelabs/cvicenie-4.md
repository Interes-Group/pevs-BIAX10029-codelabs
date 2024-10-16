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

<!-- ------------------------ -->
## Úloha 4.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, v ktorom zapúzdrite funkciu súčtu z úlohy 4.1 do funkcie
_int suma()_ . Funkciu zavolajte z hlavnej funkcie _main_, aby sa spustila. Výsledok, ktorý vráti funkcia vypíšte na obrazovku používateľovi.

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

<!-- ------------------------ -->
## Úloha 4.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, v ktorom zovšeobecnite funkciu suma z úlohy 4.3,
tak aby vrátila súčet K-tych mocnín čísel od 1 po N. Funkciu zavolajte z hlavnej funkcie _main_ s rôznymi hodnotami pre vstupný parameter.
Výsledky, ktoré vráti funkcia vypíšte na obrazovku používateľovi.

Pre voľbu parametra **k = 1** sa program správa rovnako ako predošlá verzia z úlohy 4.3.

### Príklady vstupov / výstupov programu

- pre **vstupy K = 1, N = 7** funkcia vráti číslo **28**
- pre **vstupy K = 3, N = 5** funkcia vráti číslo **225**


