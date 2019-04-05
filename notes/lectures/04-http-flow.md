# Projektowanie i implementacja zaawansowanych aplikacji PHP

## Wykład 4: HTTP Flow

### Zakres:

- HTTP Flow
    - Protokół HTTP
    - Metody HTTP
        - GET
        - HEAD
        - PUT
        - POST
        - DELETE
        - OPTIONS
        - TRACE
        - CONNECT
        - PATCH
    - Request HTTP
    - Response HTTP
        - Kody 10x, kody informacyjne
        - Kody 20x, kody sukcesu 
        - Kody 30x, kody przekierowań
        - Kody 40x, kody błędów aplikacji klienta
        - Kody 50x, kody błędów serwera HTTP
    - Nagłówki
    - Mechanizm cookies
    - Mechanizm sesji
        - Zasada działania
        - Persystencja
        - Bezpieczeństwo sesji
    - Upload plików
    - Tablice superglobalne vs PSR-7 HTTP message interfaces
- Bezpieczeństwo aplikacji webowych
    - Typowe podatności
        - Cross Site Request Forgery
        - Session Hijacking
        - Session Fixation
    - OWASP
- Wbudowany, developerski serwer HTTP
- Generowanie kodu HTML z wykorzystaniem PHP
- Mikroframeworki
    - Silex
        - Setup aplikacji
        - Routing
        - Request
        - Response
    - Wykorzystanie mikroframeworków w praktyce


### Dokumentacja

- [Sesje w PHP, dokumentacja](http://php.net/manual/en/book.session.php)
- [Cookies, dokumentacja](http://php.net/manual/en/features.cookies.php)


### Materiały uzupełniające

- [Kody HTTP](http://www.restapitutorial.com/httpstatuscodes.html)
- [Mikroframework Silex](http://silex.symfony.com)
- [Zend Expressive](https://docs.zendframework.com/zend-expressive/)


### Materiały uzupełniające, bezpieczeństwo aplikacji webowych

- [OWASP TOP 10](https://www.owasp.org/index.php/Category:OWASP_Top_Ten_Project)