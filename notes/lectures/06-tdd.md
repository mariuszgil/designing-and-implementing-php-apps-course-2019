# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Wykład 6: Test Driven Development

### Zakres:

![Piramida testów](/notes/lectures/assets/06-testing/test-pyramid.png)

- Wprowadzenie do testowania
    - Rodzaje i strategie testowania
    - Piramida testów
    - Dobór strategii testowania 
- Idea Test FIRST
    - Test FIST vs Test AFTER
        - Różnie i konswekwencje implementacji testów przed i po właściwej implementacji kodu
    - Testy jednostkowe powinny być:
        - Fast, szybkie
        - Independent, niezależne
        - Repeatable, powtarzalne
        - Self-validating, samo-walidujące się
        - Timely, pisane we właściwym momencie
- Testy jednostkowe
    - Czym jest jednostka i test jednostkowy?
    - Struktura testu jednostkowego
        - Arrange, wrowadzenie systemu w stan użliwiający przeprowadzenie testy
        - Act, wywołanie testowanej operacji
        - Assert, weryfikacja poprawności stanu
    - Strategie nazewnictwa metod testowych
    - Przygotowanie stanu
      - Metoda `setUp()`
    - Weryfikacja rezultatu
        - Asercje
    - "Uprzątnięcie" po teście
      - Metoda `tearDown()`
    - Organizacja kodu testowego
        - Wzorce organizacji
            - Testcase Class per Class
            - Testcase Class per Feature
            - Testcase Superclass
            - Parametrized Test
            - ...
    - Odcinanie zależności
        - Test Doubles
            - Dummies
            - Mocki
            - Stuby
            - Spies
            - Fakes
    - Narzędzia
        - PHPUnit
        - Prophecy
        - TestDox
- Testability kodu
    - Antywzorce i czynniki wpływające na trudność testowania kodu
        - Wysokie sprzężenie, coupling
        - Źle wykorzystany wzorzec projektowy Singleton
        - Wysoka złożoność cyklomatyczna kodu
        - Wywołania statyczne
- Test Driven Development
    - 3 prawa TDD Roberta "Uncle Boba" Martina
        - "You are not allowed to write any production code unless it is to make a failing unit test pass."
        - "You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures."
        - "You are not allowed to write any more production code than is sufficient to pass the one failing unit test."
    - Test FIRST + Refactoring
    - Cykl red-green-refactor
- Sposoby zapewniania jakości testów
  - Code Coverage vs. Branch Coverage
    - W przypadku PHPUnit wymagana jest instalacja xDebuga
  - Code Review
  - Testowanie mutacyjne
    - Weryfikacja polega na "wstrzykiwaniu" w kod programu kolejnych mutantów, a następnie uruchamianiu testów w celu sprawdzenia, czy mutant zostanie przez nie wykryty
    - Narzędzia
      - Humbug dla PHP 5.x
      - Infection dla PHP 7.1+
     
### Przykładowe programy

Przykładowy kod znajduje się w katalogu [code/06-testing](code/06-testing).

```
$ composer install
$ ./vendor/bin/phpunit
PHPUnit 7.1.1 by Sebastian Bergmann and contributors.

Runtime:       PHP 7.2.0 with Xdebug 2.6.0rc1
Configuration: designing-and-implementing-php-apps-course/notes/lectures/code/06-testing/phpunit.xml.dist

......                                                              6 / 6 (100%)

Time: 64 ms, Memory: 6.00MB

OK (6 tests, 6 assertions)
```


### Narzędzia

- [PHPUnit, dokumentacja](https://phpunit.readthedocs.io/en/latest/)
- [Prophecy, mocking framework](https://github.com/phpspec/prophecy)
- [Infection, framework dla testów mutacyjnych, bazujących na AST](https://github.com/infection/infection)
- [Humbug, framework dla testów mutacyjnych](https://github.com/humbug/humbug)
- [Xdebug, rozszerzenie wspierające debugging](https://xdebug.org)

### Materiały uzupełniające

- [XUnitPatters](http://xunitpatterns.com)
- [PHP The Right Way, Testing](http://www.phptherightway.com/#testing) 