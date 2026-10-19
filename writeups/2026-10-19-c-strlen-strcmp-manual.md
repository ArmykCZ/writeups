# Implementace vlastní logiky pro strlen a strcmp v C

## Úvod

Dnes jsem se věnoval programování v jazyce C s důrazem na **podstatu jazyka** a chování paměti. Cílem bylo opravit předchozí kód a zkusit si naprogramovat základní stringové funkce `strlen` (délka řetězce) a `strcmp` (porovnání řetězců) **bez použití standardní knihovny `<string.h>`**. Tento přístup mi pomůže lépe pochopit, jak fungují ukazatele, smyčky a detekce konce řetězce (`\0`).

## Co jsem dělal

1.  **Oprava předchozího kódu:** Projel jsem si starší implementaci a odstranil chyby v logice smyček.
2.  **Implementace `strlen` (manuální):**
    -   Vytvořil jsem funkci, která iteruje přes ukazatel na znak.
    -   Smyčka běží, dokud nenarazí na nulový znak (`\0`), který označuje konec C-řetězce.
    -   Počet iterací se ukládá jako výsledek.
3.  **Implementace `strcmp` (manuální):**
    -   Použil jsem smyčku `while`, která porovnává znaky z obou vstupních řetězců (`prvni_text[i]` a `druhy_text[i]`).
    -   Logika: Pokud jsou znaky různé, vrátím rozdíl jejich ASCII kódů a ukončím porovnání. Pokud jsou stejné, pokračuji dále.
    -   **Klíčový kód:**
        ```c
        while (prvni_text[i] != '\0' || druhy_text[i] != '\0') {
        if (prvni_text[i] != druhy_text[i]) {
            cislo = prvni_text[i] - druhy_text[i];
            printf("Cisla nejsou identicka o %d\n", cislo);
            j++;
            break;
        } else {
            i++;
        }
        ```
4.  **Zajištění konzistence:** Snažím se udržet pravidelný rytmus psaní kódu od základů, abych si udržel konzistenci v mém učení a neopíral se pouze o hotové knihovní funkce, které skryjí detaily.