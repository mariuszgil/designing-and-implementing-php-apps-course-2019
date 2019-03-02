# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Cipher

### Zadanie

Napisz program, który odczyta z parametrów przekazanych do skryptu CLI następujące informacje (w kolejności):

- znaki przeznaczone do podstawienia
- znaki podstawień
- ciąg tekstu do "zaszyfrowania"

a następnie wyświetli na standardowym wyjściu tekst, z uwzględnieniem podstawień znaków. Znaki tekstu do "zaszyfrowania" nieuwzględnione na liście podstawień powinny zostać niezmienione.


### Przykład

Wywołanie programu:

```
php cipher.php ABCE DEFX "TO JEST TEKST DO PODMIANY ABC DEF"
```

Wynik:

```
TO JXST TXKST DO PODMIDNY DEF DXF
```

### Uwagi

Program będzie uruchamiany z lini poleceń. Dostęp do argumentów wywołania skryptu jest możliwy poprzez specjalne zmienne `$argc` oraz `$argv`.


### Wskazówki

W zależności od przyjętej implementacji, pomocne mogą być funkcje przeznaczone do pracy z tablicami lub ciągami tekstowymi:

- http://php.net/manual/en/ref.array.php
- http://php.net/manual/en/ref.strings.php
