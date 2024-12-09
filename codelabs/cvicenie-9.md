summary: Cvičenie 9 Štruktúry
id: cvicenie-9
categories: cvicenie
tags: beginner
status: Published
authors: Milan Mladoniczky
feedback link: https://github.com/interes-group/pevs-BIAX10029-codelabs/issues

# Cvičenie 9 - Štruktúry

<!-- ------------------------ -->
## Úvod

Náplňou týchto úloh je precvičiť si prácu so štruktúrami v jazyku C. Úlohy sú definované pre vyskúšanie si štruktúr 
v rôznych prípadoch použitia a práce s nimi.

Pri vypracovaní úloh použite všetky doterajšie znalosti, hlavne z tématiky polí a alokovania pamäte.

### Obsah
- definovanie štruktúry
- inicializácie štruktúry
- práca s členmi štruktúry

> aside negative
> Ak používate ako vývojové prostredie lokálny a editor a následnú kompiláciu cez terminál. Použite príkaz:
> ```shell
> gcc -std=c11 -o program -Wall -Wextra main.c
> ```

týchto úloh odporúčam mať funkčné lokálne vývojové prostredie (VS Code, CLion a pod.) a kompilátor jazyka C.

> aside negative
> Nezabudnite každú alokovanú pamäť uvoľniť volaním funkcie `free` ! Je dôležité si po sebe vždy upratať.

Riešenia na jednotlivé úlohy budú uverejnené neskôr.

<!-- ------------------------ -->
## Úloha 9.1

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu študenta. 
Táto štruktúra by mala obsahovať nasledujúce položky: _meno_ (pole znakov), _vek_ (celé číslo), _priemerný prospech_ (desatinné číslo). 
Program by mal načítať údaje študentov, vypočítať priemerný vek a priemerný prospech všetkých študentov a tieto hodnoty vypísať.

Vstupy programu môžu byť zadané zo štandardného vstupu alebo načítané zo súboru.

### Príklady vstupov / výstupov programu

Pre nasledujúce vstupy programu:

```text
1. Študent
Meno: Ján 
Vek: 20 
Priemerný prospech: 1.5
---
2. Študent
Meno: Petra 
Vek: 22 
Priemerný prospech: 1.8
---
3. Študent
Meno: Milan 
Vek: 19 
Priemerný prospech: 2.0
---
```

Program vypíše na štandardný výstup nasledovný výstup:

```text
Sumár študentov:
Priemerný vek: 20.33 Priemerný prospech: 1.77
```

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

#define MAX_NAME_LENGTH 50

// Definícia štruktúry pre reprezentáciu študenta
typedef struct {
    char name[MAX_NAME_LENGTH];
    int age;
    float averageGrade;
} Student;

int main() {
    int numStudents;
    printf("Zadajte počet študentov: ");
    scanf("%d", &numStudents);

    if (numStudents <= 0) {
        printf("Počet študentov musí byť kladné číslo.\n");
        return 1;
    }

    // Dynamická alokácia poľa študentov
    Student *students = (Student *)malloc(numStudents * sizeof(Student));
    if (students == NULL) {
        printf("Nepodarilo sa alokovať pamäť.\n");
        return 1;
    }

    // Načítanie údajov študentov
    for (int i = 0; i < numStudents; i++) {
        printf("\n%d. Študent\n", i + 1);
        printf("Meno: ");
        scanf(" %49s", students[i].name); // Obmedzenie na MAX_NAME_LENGTH - 1 znakov
        printf("Vek: ");
        scanf("%d", &students[i].age);
        printf("Priemerný prospech: ");
        scanf("%f", &students[i].averageGrade);
    }

    // Výpočet priemerného veku a priemerného prospechu
    float totalAge = 0, totalGrade = 0;
    for (int i = 0; i < numStudents; i++) {
        totalAge += students[i].age;
        totalGrade += students[i].averageGrade;
    }

    float averageAge = totalAge / numStudents;
    float averageGrade = totalGrade / numStudents;

    // Výpis výsledkov
    printf("\nSumár študentov:\n");
    printf("Priemerný vek: %.2f\n", averageAge);
    printf("Priemerný prospech: %.2f\n", averageGrade);

    // Uvoľnenie pamäte
    free(students);

    return 0;
}
```

#### Vysvetlenie

1. Definícia štruktúry:
   * Štruktúra Student obsahuje položky name (pole znakov), age (vek), a averageGrade (priemerný prospech).

2. Načítanie počtu študentov:
   * Používateľ zadáva počet študentov.
   * Pamäť pre pole študentov je dynamicky alokovaná pomocou malloc.

3. Načítanie údajov:
   * V cykle sa načítavajú údaje pre každého študenta.
   * Funkcia scanf obmedzuje dĺžku vstupu pre meno na maximálne 49 znakov (jeden znak je rezervovaný pre \0).

4. Výpočty:
   * Po načítaní údajov sa vypočíta priemerný vek a priemerný prospech pomocou súčtov všetkých hodnôt.

5. Výpis a uvoľnenie pamäte:
   * Priemerné hodnoty sú vypísané s presnosťou na dve desatinné miesta.
   * Dynamicky alokovaná pamäť sa uvoľní pomocou free.

<!-- ------------------------ -->
## Úloha 9.2

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu zamestnanca. 
Štruktúra by mala obsahovať _meno_ (pole znakov), _identifikačné číslo_ (celé číslo) a _plat_ (desatinné číslo). 
Program by mal načítať údaje pre niekoľko zamestnancov, zoradiť ich podľa platu zostupne a 
vypísať zoznam zamestnancov spolu s ich platmi. Následne program vypíše priemerný plat zamestnancov.

Údaje o zamestnancoch načítajte zo súboru, kde na jednom riadku je definovaný jeden zamestnanec a hodnoty na riadku sú oddelené medzerou: `ID Meno Plat`

Cestu k súboru načítajte od používateľa zo štandardného vstupu na začiatku programu.

### Príklady vstupov / výstupov programu

Program pre vstupný súbor:

```text
101 Anna 2500.50
102 Peter 3000.75
103 Lucia 2800.00
```

vypíše nasledovný text na výstupe:

```text
102 Peter 3000.75
103 Lucia 2800.00
101 Anna 2500.50
---
Priemerný plat: 2767.08
```

### Bonus

Skúste upraviť výpis tak aby mal formát tabuľky. Nezabudnite na správne zarovnanie stĺpcov. Takýto výstup by mohol vyzerať nasledovne:

```text
|ID  |Meno  |Plat    |
|----|------|--------|
|102 |Peter |3000.75 |
|103 |Lucia |2800.00 |
|101 |Anna  |2500.50 |
---
Priemerný plat: 2767.08
```

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_NAME_LENGTH 50
#define MAX_EMPLOYEES 100

// Definícia štruktúry na reprezentáciu zamestnanca
typedef struct {
    int id;
    char name[MAX_NAME_LENGTH];
    float salary;
} Employee;

// Funkcia na porovnanie zamestnancov podľa platu (pre qsort)
int compareBySalaryDescending(const void *a, const void *b) {
    float salaryA = ((Employee *)a)->salary;
    float salaryB = ((Employee *)b)->salary;
    if (salaryA < salaryB) return 1;
    if (salaryA > salaryB) return -1;
    return 0;
}

int main() {
    char filePath[100];
    Employee employees[MAX_EMPLOYEES];
    int count = 0;

    // Načítanie cesty k súboru
    printf("Zadajte cestu k súboru: ");
    scanf("%s", filePath);

    // Otvorenie súboru
    FILE *file = fopen(filePath, "r");
    if (file == NULL) {
        printf("Nepodarilo sa otvoriť súbor.\n");
        return 1;
    }

    // Načítanie údajov zo súboru
    while (fscanf(file, "%d %49s %f", &employees[count].id, employees[count].name, &employees[count].salary) == 3) {
        count++;
        if (count >= MAX_EMPLOYEES) {
            printf("Dosiahnutý maximálny počet zamestnancov (%d).\n", MAX_EMPLOYEES);
            break;
        }
    }
    fclose(file);

    if (count == 0) {
        printf("Súbor neobsahuje žiadne údaje o zamestnancoch.\n");
        return 1;
    }

    // Zoradenie zamestnancov podľa platu zostupne
    qsort(employees, count, sizeof(Employee), compareBySalaryDescending);

    // Výpočet priemerného platu
    float totalSalary = 0;
    for (int i = 0; i < count; i++) {
        totalSalary += employees[i].salary;
    }
    float averageSalary = totalSalary / count;

    // Výpis zamestnancov
    printf("\n");
    for (int i = 0; i < count; i++) {
        printf("%d %s %.2f\n", employees[i].id, employees[i].name, employees[i].salary);
    }

    // Výpis priemerného platu
    printf("---\n");
    printf("Priemerný plat: %.2f\n", averageSalary);

    return 0;
}
```

#### Vysvetlenie

1. Definícia štruktúry:
   * Štruktúra Employee obsahuje ID, meno a plat zamestnanca.

2. Načítanie údajov zo súboru:
   * Súbor je otvorený v režime čítania pomocou fopen.
   * Hodnoty sú načítané pomocou fscanf, kde sa očakáva formát ID Meno Plat.

3. Kontrola limitov:
   * Ak súbor neobsahuje údaje alebo je dosiahnutý maximálny počet zamestnancov (MAX_EMPLOYEES), program končí s príslušnou správou.

4. Zoradenie:
   * qsort zoradí zamestnancov podľa platu v zostupnom poradí pomocou funkcie compareBySalaryDescending.

5. Výpočet priemerného platu:
   * Priemerný plat sa vypočíta ako súčet platov všetkých zamestnancov delený ich počtom.

6. Výpis výsledkov:
   * Zoradení zamestnanci sú vypísaní spolu s ich ID, menom a platom.
   * Priemerný plat je vypísaný s presnosťou na dve desatinné miesta.

7. Uvoľnenie zdrojov:
   * Súbor je zavretý po načítaní údajov.

<!-- ------------------------ -->
## 🗓️ Úloha 9.3

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý definuje štruktúru na reprezentáciu dátumu s položkami _deň_, 
_mesiac_ a _rok_ (celé čísla). Program by mal umožniť používateľovi zadať dva dátumy kde jednotlivé hodnoty dátumov sú definované v jednom riadku oddelené medzerou
a vypočítať rozdiel medzi nimi. Rozdieľ je vypísaný ako počet dní medzi dátumami.

V programe ošetrite vstup od používateľa aby bolo možné zadať iba správny dátum (napríklad nie je možné zadať 31.2.) a zohľadňuje priestupné roky.

### Príklady vstupov / výstupov programu

Priebeh programu môže vyzerať nasledovne:

```text
Prvý dátum: 1 1 2023
Druhý dátum: 15 1 2024
---
Rozdiel dátumov: 376 dní
```

```text
Prvý dátum: 28 2 2020
Druhý dátum: 1 3 2020
---
Rozdiel dátumov: 2 dni
```

### Bonus

Skúste upraviť výpis rozdielu dátumov tak aby uviedol pre používateľa rozdiel aj koľko prípadných rokov, mesiacov, či dní je medzi dátumami. Napríklad:

- vstup: 1.1.2023 a 15.1.2024 -> 1 rok a 15 dní
- vstup: 1.1.2022 a 5.3.2022 -> 2 mesiace a 5 dní

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

// Štruktúra na reprezentáciu dátumu
typedef struct {
    int day;
    int month;
    int year;
} Date;

// Počet dní v mesiacoch (pre bežné a priestupné roky)
const int daysInMonth[2][12] = {
    {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}, // Bežný rok
    {31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31}  // Priestupný rok
};

// Funkcia na kontrolu, či je rok priestupný
int isLeapYear(int year) {
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}

// Funkcia na validáciu dátumu
int isValidDate(Date date) {
    if (date.year < 1 || date.month < 1 || date.month > 12 || date.day < 1) {
        return 0;
    }
    int leap = isLeapYear(date.year);
    if (date.day > daysInMonth[leap][date.month - 1]) {
        return 0;
    }
    return 1;
}

// Funkcia na prepočet dátumu na počet dní od začiatku referenčného bodu (napr. 1.1.0001)
int dateToDays(Date date) {
    int totalDays = 0;

    // Pridanie dní za celé roky
    for (int i = 1; i < date.year; i++) {
        totalDays += isLeapYear(i) ? 366 : 365;
    }

    // Pridanie dní za celé mesiace v aktuálnom roku
    int leap = isLeapYear(date.year);
    for (int i = 0; i < date.month - 1; i++) {
        totalDays += daysInMonth[leap][i];
    }

    // Pridanie dní v aktuálnom mesiaci
    totalDays += date.day;

    return totalDays;
}

// Funkcia na výpočet rozdielu medzi dvoma dátumami
int calculateDateDifference(Date date1, Date date2) {
    int days1 = dateToDays(date1);
    int days2 = dateToDays(date2);
    return abs(days1 - days2);
}

int main() {
    Date date1, date2;

    // Načítanie prvého dátumu
    printf("Prvý dátum (deň mesiac rok): ");
    scanf("%d %d %d", &date1.day, &date1.month, &date1.year);
    if (!isValidDate(date1)) {
        printf("Neplatný dátum! Zadajte správny dátum.\n");
        return 1;
    }

    // Načítanie druhého dátumu
    printf("Druhý dátum (deň mesiac rok): ");
    scanf("%d %d %d", &date2.day, &date2.month, &date2.year);
    if (!isValidDate(date2)) {
        printf("Neplatný dátum! Zadajte správny dátum.\n");
        return 1;
    }

    // Výpočet a výpis rozdielu
    int difference = calculateDateDifference(date1, date2);
    printf("---\nRozdiel dátumov: %d dní\n", difference);

    return 0;
}
```

#### Vysvetlenie

1. Štruktúra Date:
   * Reprezentuje dátum s položkami day, month a year.

2. Priestupný rok:
   * Funkcia isLeapYear kontroluje, či je rok priestupný, na základe pravidiel pre gregoriánsky kalendár.

3. Validácia dátumu:
   * Funkcia isValidDate overuje, či zadaný dátum je platný (správny rozsah dní, mesiacov a rokov).

4. Prepočet dátumu na počet dní:
   * Funkcia dateToDays konvertuje dátum na celkový počet dní od referenčného bodu (1.1.0001).
   * Zahŕňa dni za celé roky, mesiace a aktuálny deň.

5. Rozdiel medzi dátumami:
   * Funkcia calculateDateDifference vypočíta rozdiel v počte dní medzi dvoma dátumami.

6. Hlavný program:
   * Používateľ zadá dva dátumy, ktoré sa validujú.
   * Po výpočte rozdielu v dňoch je výsledok vypísaný.

<!-- ------------------------ -->
## 📚 Úloha 9.4

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý vytvorí štruktúru na reprezentáciu knihy v knižnici. 
Štruktúra by mala obsahovať _názov_ (pole znakov), _autora_ (pole znakov) a _rok vydania_ (celé číslo). 
Program by mal načítať údaje zo súboru kde je definovaná kniha na jednom riadku a hodnoty štruktúry sú oddelené bodkočiarkou.
Vstupný súbor môže byť v rovnakom priečinku ako program a môže mať napevno definovaný názov v zdrojovom kóde.
Program po úspešnom spracovaní súboru vypíše počet načítaných kníh.
Program následne umožní zadať používateľovi rok a vypíše knihy, ktoré boli vydané v zadanom roku.

### Príklady vstupov / výstupov programu

Vstupný súbor s knihami

```text
Programovanie v C;Kernighan & Ritchie;1988  
Moderné algoritmy;Jon Bentley;1990  
Umenie programovania;Donald Knuth;1968  
Štruktúra a interpretácia počítačových programov;Harold Abelson & Gerald Jay Sussman;1985  
Cvičenia z programovania;Brian Kernighan;1988  
Algoritmy v C++;Robert Sedgewick;1990  
Čistý kód;Robert C. Martin;2008  
Pragmatický programátor;Andrew Hunt & David Thomas;1999  
Python pre začiatočníkov;Guido van Rossum;2000  
Počítačová grafika;John F. Hughes & James D. Foley;1995  
```

Priebeh programu môže byť nasledovný:

```text
Počet kníh v databáze: 10
Zadajte rok vydania kníh: 1990

Názov: Moderné algoritmy
Autor: Jon Bentley
Rok vydania: 1990
---
Názov: Algoritmy v C++
Autor: Robert Sedgewick
Rok vydania: 1990
```

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_TITLE_LENGTH 100
#define MAX_AUTHOR_LENGTH 100
#define MAX_BOOKS 100

// Štruktúra na reprezentáciu knihy
typedef struct {
    char title[MAX_TITLE_LENGTH];
    char author[MAX_AUTHOR_LENGTH];
    int year;
} Book;

// Funkcia na načítanie údajov zo súboru
int loadBooks(const char *filename, Book books[]) {
    FILE *file = fopen(filename, "r");
    if (file == NULL) {
        printf("Nepodarilo sa otvoriť súbor %s.\n", filename);
        return -1;
    }

    int count = 0;
    char line[256];
    while (fgets(line, sizeof(line), file)) {
        if (count >= MAX_BOOKS) {
            printf("Dosiahnutý maximálny počet kníh (%d).\n", MAX_BOOKS);
            break;
        }

        // Odstránenie nového riadku na konci
        line[strcspn(line, "\n")] = '\0';

        // Rozdelenie riadku podľa bodkočiarky
        char *token = strtok(line, ";");
        if (token != NULL) {
            strncpy(books[count].title, token, MAX_TITLE_LENGTH - 1);
            books[count].title[MAX_TITLE_LENGTH - 1] = '\0';
        }

        token = strtok(NULL, ";");
        if (token != NULL) {
            strncpy(books[count].author, token, MAX_AUTHOR_LENGTH - 1);
            books[count].author[MAX_AUTHOR_LENGTH - 1] = '\0';
        }

        token = strtok(NULL, ";");
        if (token != NULL) {
            books[count].year = atoi(token);
        }

        count++;
    }

    fclose(file);
    return count;
}

// Funkcia na vyhľadanie a výpis kníh podľa roku
void printBooksByYear(Book books[], int count, int year) {
    int found = 0;
    for (int i = 0; i < count; i++) {
        if (books[i].year == year) {
            printf("Názov: %s\n", books[i].title);
            printf("Autor: %s\n", books[i].author);
            printf("Rok vydania: %d\n", books[i].year);
            printf("---\n");
            found = 1;
        }
    }

    if (!found) {
        printf("Žiadne knihy z roku %d.\n", year);
    }
}

int main() {
    Book books[MAX_BOOKS];
    const char *filename = "books.txt";

    // Načítanie kníh zo súboru
    int bookCount = loadBooks(filename, books);
    if (bookCount < 0) {
        return 1; // Chyba pri načítaní
    }

    printf("Počet kníh v databáze: %d\n", bookCount);

    // Zadanie roku od používateľa
    int year;
    printf("Zadajte rok vydania kníh: ");
    scanf("%d", &year);

    // Výpis kníh podľa roku
    printBooksByYear(books, bookCount, year);

    return 0;
}
```

#### Vysvetlenie

1. Štruktúra Book:
   * Obsahuje názov knihy, autora a rok vydania.

2. Načítanie zo súboru:
   * Funkcia loadBooks otvára súbor books.txt a načítava knihy po riadkoch.
   * Každý riadok je rozdelený na časti (title, author, year) pomocou strtok.
   * Maximálny počet kníh je obmedzený na MAX_BOOKS.

3. Vyhľadanie podľa roku:
   * Funkcia printBooksByYear prechádza zoznam kníh a vypisuje knihy, ktoré zodpovedajú zadanému roku.

4. Hlavný program:
   * Načítava knihy zo súboru.
   * Vypisuje počet kníh v databáze.
   * Umožňuje používateľovi zadať rok a zobrazí zodpovedajúce knihy.

<!-- ------------------------ -->
## ⛓️‍💥 Úloha 9.5

Napíšte program, zdrojový kód, v jazyku C použitím štandardu C11, ktorý implementuje jednoduchý zreťazený zoznam pomocou štruktúr. 
Každý prvok zoznamu by mal obsahovať celé kladné číslo a pointer na ďalší prvok.
Program umožní používateľovi cez štandardný vstup zadať číslo prvku zoznamu. Po zadaní vstupu je nový prvok pridaný na koniec zoznamu
a následne vypíše celý aktuálny zoznam a znova ponúkne používateľovi zadať ďalší prvok.
Program končí ak používateľ na vstupe zadá hodnotu -1.

> aside negative
> Nezabudnite uvoľniť pamäť alokovanú pre jednotlivé prvky zoznamu na konci programu!

### Príklady vstupov / výstupov programu

Priebeh programu môže vyzerať nasledovne:

```text
---
Zadajte hodnotu prvku: 1
Aktuálny zoznam: 1
---
Zadajte hodnotu prvku: 85
Aktuálny zoznam: 1, 85
---
Zadajte hodnotu prvku: 423
Aktuálny zoznam: 1, 85, 423
---
Zadajte hodnotu prvku: -1
```

### Riešenie

```C
#include <stdio.h>
#include <stdlib.h>

// Štruktúra pre uzol zreťazeného zoznamu
typedef struct Node {
    int value;
    struct Node *next;
} Node;

// Funkcia na vytvorenie nového uzla
Node* createNode(int value) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    if (newNode == NULL) {
        printf("Nepodarilo sa alokovať pamäť pre nový uzol.\n");
        exit(1);
    }
    newNode->value = value;
    newNode->next = NULL;
    return newNode;
}

// Funkcia na pripojenie uzla na koniec zoznamu
void appendNode(Node** head, int value) {
    Node* newNode = createNode(value);

    if (*head == NULL) {
        // Ak je zoznam prázdny, nový uzol sa stane hlavou
        *head = newNode;
    } else {
        // Inak nájdeme posledný uzol a pripojíme nový uzol
        Node* current = *head;
        while (current->next != NULL) {
            current = current->next;
        }
        current->next = newNode;
    }
}

// Funkcia na výpis zoznamu
void printList(Node* head) {
    Node* current = head;
    if (current == NULL) {
        printf("Zoznam je prázdny.\n");
        return;
    }
    while (current != NULL) {
        printf("%d", current->value);
        if (current->next != NULL) {
            printf(", ");
        }
        current = current->next;
    }
    printf("\n");
}

// Funkcia na uvoľnenie pamäte zoznamu
void freeList(Node* head) {
    Node* current = head;
    while (current != NULL) {
        Node* temp = current;
        current = current->next;
        free(temp);
    }
}

int main() {
    Node* head = NULL; // Hlava zoznamu
    int input;

    while (1) {
        printf("\nZadajte hodnotu prvku (-1 pre ukončenie): ");
        scanf("%d", &input);

        if (input == -1) {
            break;
        }

        if (input < 0) {
            printf("Zadajte iba kladné čísla alebo -1 pre ukončenie.\n");
            continue;
        }

        // Pridanie nového prvku do zoznamu
        appendNode(&head, input);

        // Výpis aktuálneho zoznamu
        printf("Aktuálny zoznam: ");
        printList(head);
    }

    // Uvoľnenie pamäte
    freeList(head);
    printf("Pamäť bola uvoľnená. Program ukončený.\n");

    return 0;
}
```

#### Vysvetlenie

1. Štruktúra Node:
   * Reprezentuje uzol zoznamu, obsahuje hodnotu (value) a pointer na ďalší uzol (next).

2. Vytvorenie uzla:
   * Funkcia createNode alokuje pamäť pre nový uzol a inicializuje ho hodnotou.

3. Pripojenie uzla na koniec zoznamu:
   * Funkcia appendNode pridá nový uzol na koniec zoznamu.
   * Ak je zoznam prázdny, nový uzol sa stane hlavou.

4. Výpis zoznamu:
   * Funkcia printList prechádza zoznam a vypisuje hodnoty jednotlivých uzlov.

5. Uvoľnenie pamäte:
   * Funkcia freeList prejde všetky uzly zoznamu a uvoľní ich pamäť.

6. Hlavný program:
   * Používateľ opakovane zadáva hodnoty, ktoré sa pridávajú do zoznamu.
   * Po každom pridaní sa vypíše aktuálny stav zoznamu.
   * Program končí, keď používateľ zadá -1.
