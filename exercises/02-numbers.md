# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Numbers

### Zadanie

Zaprojektuj, a następnie zaimplementuj klasę Number reprezentującą liczbę w zadanym systemie (binarnym, ósemkowym, dziesiętnym, szesnastkowym, etc). Klasa ta powinna umożliwiać następujące operacje:

- zainicjalizowanie liczby w określonym systemie
- konwersję liczby do innego systemu, z uwzględnieniem konceptu immutability obiektu
    - w wyniku wywołania tej metody powinnien zostać zwrócony nowy obiekt, w docelowym systemie liczbowym
- dodanie innej liczby, z uwzględnieniem konceptu immutability obiektu
    - w wyniku wywołania tej metody powinnien zostać zwrócony nowy obiekt opisujący sumę
   
Zaprojektuj, a następnie zaimplementuj:

- interfejs NumberFormatter, przeznaczony do formatowania liczby do łańchua tekstowego
- klasę RomanFormatter implementującą interfejs NumberFormatter, formatującą podaną liczbę z użyciem systemu rzymskiego

Napisz program, który odczyta z parametrów wejściowych serię liczb wraz z systemem ich zapisu, zsumuje je, a następnie wyświetli wynik w zapisie rzymskim. 

Liczby będą podawane w postaci `liczba:system`.


### Przykład

Wywołanie programu:

```
php numbers.php "1010:2" "10:10" "10:16"
```

Wynik:

```
XXXVI
```

### Uwagi

Program będzie uruchamiany z lini poleceń. Dostęp do argumentów wywołania skryptu jest możliwy poprzez specjalne zmienne `$argc` oraz `$argv`.
