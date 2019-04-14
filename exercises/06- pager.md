# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Pager

### Wprowadzenie

Typowym elementem aplikacji webowych jest komponent pagera, który umożliwia nawigowanie po długich listingach obiektów w systemie. Zazwyczaj przedstawiany jest on w postaci zestawu linków prowadzących do odpowiednich podstron listingu:

`<PREV-PAGE-LINK> 1 ... 10 11 12 ... 66 <NEXT PAGE LINK>`

Zestaw wyświetlonych linków może być różny w zależności od danych wejściowych, w ogólnym przypadku zawiera on odnośniki do następujących stron listingu (pozostałe linki są ukrywane):

- pierwszej
- ostatniej
- poprzedzającej aktualną
- aktualnej
- następującą po aktualnej


### Zadanie

Zaprojektuj klasę (lub klasy) umożlwiające zbudowanie pagera (bez warstwy prezentacji w HTML!), który przyjmować będzie na wejściu następujące dane:

- łączną liczbę obiektów
- liczbę obiektów na 1 stronie
- number bieżącej strony lub offset wyrażony liczbą wyświetlonych już obiektów (do wyboru)

Pager powinien odpowiadać na następujące zapytania:

- ile jest łącznie stron?
- czy linki do poprzeniej/następnej strony są widoczne?
- jakie linki powinny zostać wyświetlone?

Zaimplementuj zestaw testów jednostkowych w wykorzystaniem biblioteki PHPUnit, weryfikujących działanie pagera.


### Uwaga

Przez "link" można rozumieć numer strony.


### Opcjonalne rozszerzenie zadania (5 pkt)

Wykorzystując bibliotekę do testów mutacyjnych Infection, zweryfikuj jakość zaimplementowanych testów. Warunkiem uzyskania dodatkowych punktów jest uruchomienie Infection, zaprezentowanie oraz krótkie omówienie raportu wynikowego.

Do uruchomienia Infection wymagana będzie obecność rozszerzenie Xdebug.