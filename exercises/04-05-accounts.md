# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Accounts

### Wprowadzenie

System obsługuje konta w systemie gamifikacyjnym, gdzie za wykonywanie pewnych akcji użytkownicy otrzymują punkty. Następnie punkty te mogą zostać "wydane" w ramach akcji podejmowanych przez użytkownika w systemie.
 
Zespół podjął decyzję, aby funkcjonalność ta była obsługiwana przez dedykowany mikroserwis, udostępniający interfejs HTTP REST. Mikroserwis ten będzie wykorzystywany zarówno we flow pracy normalnego użytkownika, ale także z poziomu aplikacji back-office'owych systemu.


### Zadanie

#### Część 1

- Zaprojektuj interfejs REST mikroserwisu pozwalającego na zarządzanie kontami i punktami w systemie gamifikacyjnym. Powinien on udostępniać następujące operacje:
    - Założenie konta, gdzie każde konto posiada następujące informacje:
        - ID
        - email
        - opcjonalny opis
        - balans punktów
        - status (aktywne/zablokowane)
    - Zasilenie konta wskazaną liczbą punktów
    - Zwrócenie informacji o koncie, jego saldzie
    - Zwrócenie informacji o wszystkich kontach w systemie
        - Dla uproszczenia, nie należy się przejmować zagadnieniem dużej ilości kont w systemie
    - Zablokowanie/odblokowanie konta  
- Zaimplementuj zaprojektowany interfejs w jednym z wybranych przez siebie mikroframeworków PHP
    - Silex
    - SlimPHP
    - ...
- Formatem wymiany danych jest JSON

 
#### Część 2

- Zaimplementuj osobną aplikację, której zadaniem będzie wyświetlenie listy dostępnych kont w systemie
- Aplikacja powinna wystawić 1 endpoint, którego wywołanie skutkować będzie pobraniem listy kont z mikroserwisu, a następnie wyrenderowanie HTML z użyciem systemu szablonów Twig
- Aplikacja powinna być wyposażona w 2 szablony:
    - master template, zawierający bazowy układ HTML całej strony, z uwzględnieniem np. sekcji HEAD
    - listing template, zawierający jedynie kod HTML listy kont


### Uwaga

Za pełną implementację zadania można otrzymać 20 punktów, po 10 za każdą z części. Część 2 może zostać zaimplementowana bez części 1, w tym celu należy pobierać statyczny plik zawierający dane kont w formacie JSON.


### Wskazówki

- Komunikację pomiędzy aplikacjami można oprzeć np. o:
    - [Bibliotekę Guzzle](http://docs.guzzlephp.org/en/stable/quickstart.html#making-a-request)
    - [Bibliotekę Clien URL](https://www.php.net/manual/en/book.curl.php)
    - [Funkcję file_get_contents](https://www.php.net/manual/en/function.file-get-contents.php), ale uwaga! To rozwiązanie nie nadaje się do zastosowań produkcyjnych i może być niebezpieczne!   


### Dodatkowe wymagania

- Każdy z zaimplementowanych elementów, tj. interfejsów, klas, traitów (jeśli istnieją) powinny zostać umieszczone w osobnym pliku, zgodnie z rekomendacją PSR-4
    - Zaproponuj odpowiednią strukturę namespace'ów
- Staraj się postępować zgodnie z zasadami SOLID
- Program demonstracyjny powinien wykorzystać mechanizmy Composera do ładowania poszczególnych klas i interfejsów


### Uwagi

Do uruchomienia obu programów nie będzie potrzebny osobny webserwer typu Apache lub Nginx. Wbudowany w [PHP developerski serwer www](https://www.php.net/manual/en/features.commandline.webserver.php) będzie tu całkowicie wystarczający.